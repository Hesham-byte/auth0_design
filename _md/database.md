# Cognitive Sanctuary Database Schema

## Overview
Educational AI platform with Auth0-secured token vault, AI tutoring sessions, progress tracking, and resource management.

---

## Core Tables

### `users`
Platform users (students, teachers, admins).

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY, DEFAULT gen_random_uuid() | User identifier |
| `auth0_id` | VARCHAR(255) | UNIQUE, NOT NULL | Auth0 user ID |
| `email` | VARCHAR(255) | UNIQUE, NOT NULL | User email |
| `first_name` | VARCHAR(100) | NOT NULL | First name |
| `last_name` | VARCHAR(100) | NOT NULL | Last name |
| `role` | ENUM | DEFAULT 'student' | student, teacher, admin |
| `status` | ENUM | DEFAULT 'active' | active, suspended, inactive |
| `avatar_url` | VARCHAR(500) | NULL | Profile image URL |
| `institution_id` | UUID | FK → institutions.id | User's school/university |
| `last_active_at` | TIMESTAMP | NULL | Last activity timestamp |
| `last_ip_address` | INET | NULL | Last known IP |
| `created_at` | TIMESTAMP | DEFAULT NOW() | Account creation |
| `updated_at` | TIMESTAMP | DEFAULT NOW() | Last update |

**Indexes:** `email`, `auth0_id`, `role`, `status`, `institution_id`

---

### `institutions`
Schools, universities, or organizations.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Institution ID |
| `name` | VARCHAR(255) | NOT NULL | Institution name |
| `domain` | VARCHAR(255) | UNIQUE | Email domain (e.g., university.edu) |
| `license_tier` | ENUM | DEFAULT 'basic' | basic, standard, premium |
| `created_at` | TIMESTAMP | DEFAULT NOW() | Creation date |

---

### `subjects`
Academic subjects available in the platform.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Subject ID |
| `name` | VARCHAR(100) | UNIQUE, NOT NULL | e.g., "Mathematics", "Physics" |
| `slug` | VARCHAR(100) | UNIQUE, NOT NULL | URL-friendly identifier |
| `icon` | VARCHAR(50) | NULL | Material icon name |
| `color` | VARCHAR(7) | DEFAULT '#2b3896' | Hex color code |
| `description` | TEXT | NULL | Subject description |
| `created_at` | TIMESTAMP | DEFAULT NOW() | Creation date |

---

### `topics`
Specific topics within subjects.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Topic ID |
| `subject_id` | UUID | FK → subjects.id | Parent subject |
| `name` | VARCHAR(200) | NOT NULL | Topic name |
| `slug` | VARCHAR(200) | NOT NULL | URL-friendly |
| `difficulty_level` | SMALLINT | DEFAULT 1 | 1-5 difficulty scale |
| `created_at` | TIMESTAMP | DEFAULT NOW() | Creation date |

**Indexes:** `subject_id`

---

## Session Management

### `sessions`
AI tutoring sessions between users and the AI agent.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Session ID |
| `user_id` | UUID | FK → users.id, NOT NULL | Student user |
| `title` | VARCHAR(255) | NOT NULL | Session title |
| `subject_id` | UUID | FK → subjects.id | Related subject |
| `topic_id` | UUID | FK → topics.id | Specific topic |
| `description` | TEXT | NULL | Session summary |
| `accuracy_score` | DECIMAL(5,2) | NULL | 0-100% accuracy |
| `status` | ENUM | DEFAULT 'active' | active, completed, archived |
| `started_at` | TIMESTAMP | DEFAULT NOW() | Session start |
| `ended_at` | TIMESTAMP | NULL | Session end |
| `duration_minutes` | INTEGER | NULL | Total duration |
| `token_usage` | INTEGER | DEFAULT 0 | AI tokens consumed |
| `context_id` | VARCHAR(255) | NULL | External AI context ref |

**Indexes:** `user_id`, `subject_id`, `started_at`, `status`

---

### `session_messages`
Individual messages within a session.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Message ID |
| `session_id` | UUID | FK → sessions.id, NOT NULL | Parent session |
| `role` | ENUM | NOT NULL | user, assistant, system |
| `content` | TEXT | NOT NULL | Message content |
| `metadata` | JSONB | NULL | Token counts, model info |
| `created_at` | TIMESTAMP | DEFAULT NOW() | Message timestamp |

**Indexes:** `session_id`, `created_at`

---

## Progress & Analytics

### `user_progress`
Student progress tracking per subject.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Progress record ID |
| `user_id` | UUID | FK → users.id, NOT NULL | Student |
| `subject_id` | UUID | FK → subjects.id, NOT NULL | Subject |
| `completion_percentage` | DECIMAL(5,2) | DEFAULT 0 | 0-100% complete |
| `proficiency_score` | DECIMAL(5,2) | DEFAULT 0 | Mastery level 0-100 |
| `sessions_completed` | INTEGER | DEFAULT 0 | Count of sessions |
| `total_study_time` | INTEGER | DEFAULT 0 | Minutes studied |
| `last_session_at` | TIMESTAMP | NULL | Last activity |
| `created_at` | TIMESTAMP | DEFAULT NOW() | Record creation |
| `updated_at` | TIMESTAMP | DEFAULT NOW() | Last update |

**Indexes:** `user_id`, `subject_id`
**Unique:** `(user_id, subject_id)`

---

### `engagement_metrics`
Daily/periodic engagement analytics.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Metric ID |
| `user_id` | UUID | FK → users.id | Student (NULL for aggregate) |
| `institution_id` | UUID | FK → institutions.id | Institution |
| `date` | DATE | NOT NULL | Metric date |
| `sessions_count` | INTEGER | DEFAULT 0 | Sessions started |
| `messages_count` | INTEGER | DEFAULT 0 | Messages exchanged |
| `study_minutes` | INTEGER | DEFAULT 0 | Time spent |
| `resources_accessed` | INTEGER | DEFAULT 0 | Resources viewed |
| `cognitive_load_score` | DECIMAL(4,2) | NULL | 0-10 difficulty metric |

**Indexes:** `user_id`, `institution_id`, `date`

---

## Resource Library

### `resources`
Educational materials (PDFs, videos, labs).

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Resource ID |
| `title` | VARCHAR(255) | NOT NULL | Resource title |
| `description` | TEXT | NULL | Description |
| `type` | ENUM | NOT NULL | pdf, video, interactive, link |
| `subject_id` | UUID | FK → subjects.id | Related subject |
| `topic_id` | UUID | FK → topics.id | Specific topic |
| `author_id` | UUID | FK → users.id | Creator (teacher/admin) |
| `institution_id` | UUID | FK → institutions.id | Owning institution |
| `file_url` | VARCHAR(500) | NULL | File location |
| `file_size_bytes` | BIGINT | NULL | File size |
| `duration_seconds` | INTEGER | NULL | Video/audio length |
| `thumbnail_url` | VARCHAR(500) | NULL | Preview image |
| `is_featured` | BOOLEAN | DEFAULT FALSE | Featured content |
| `is_secure` | BOOLEAN | DEFAULT FALSE | Vault-secured resource |
| `access_count` | INTEGER | DEFAULT 0 | View/download count |
| `status` | ENUM | DEFAULT 'published' | draft, published, archived |
| `created_at` | TIMESTAMP | DEFAULT NOW() | Creation date |
| `updated_at` | TIMESTAMP | DEFAULT NOW() | Last update |

**Indexes:** `subject_id`, `type`, `status`, `is_featured`, `author_id`

---

### `resource_tags`
Tags for resource categorization.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Tag ID |
| `name` | VARCHAR(50) | UNIQUE, NOT NULL | Tag name |
| `color` | VARCHAR(7) | DEFAULT '#757684' | Tag color |

---

### `resource_tag_mappings`
Many-to-many resource tags.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `resource_id` | UUID | FK → resources.id | Resource |
| `tag_id` | UUID | FK → resource_tags.id | Tag |

**PK:** `(resource_id, tag_id)`

---

## Token Vault & Security

### `vault_configurations`
Auth0 and encryption configurations per institution.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Config ID |
| `institution_id` | UUID | FK → institutions.id, UNIQUE | Institution |
| `auth0_domain` | VARCHAR(255) | NOT NULL | e.g., sanctuary.us.auth0.com |
| `auth0_client_id` | VARCHAR(255) | NOT NULL | Auth0 client ID |
| `auth0_client_secret_encrypted` | TEXT | NOT NULL | Encrypted secret |
| `jwks_uri` | VARCHAR(500) | NULL | JWKS endpoint |
| `encryption_key_id` | VARCHAR(100) | NOT NULL | Current key identifier |
| `encryption_algorithm` | VARCHAR(20) | DEFAULT 'AES-256-GCM' | Encryption method |
| `last_key_rotation_at` | TIMESTAMP | NULL | Last rotation |
| `auto_rotate_days` | INTEGER | DEFAULT 90 | Rotation schedule |
| `created_at` | TIMESTAMP | DEFAULT NOW() | Creation |
| `updated_at` | TIMESTAMP | DEFAULT NOW() | Last update |

---

### `api_endpoints`
Secure external API integrations.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Endpoint ID |
| `institution_id` | UUID | FK → institutions.id | Institution |
| `provider_name` | VARCHAR(100) | NOT NULL | e.g., "WolframAlpha" |
| `endpoint_url` | VARCHAR(500) | NOT NULL | API URL |
| `api_key_encrypted` | TEXT | NULL | Encrypted API key |
| `is_active` | BOOLEAN | DEFAULT TRUE | Status |
| `rate_limit_per_minute` | INTEGER | DEFAULT 60 | Rate limit |
| `last_used_at` | TIMESTAMP | NULL | Last access |
| `created_at` | TIMESTAMP | DEFAULT NOW() | Creation |

**Indexes:** `institution_id`, `is_active`

---

### `security_audit_logs`
Security and activity audit trail.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Log ID |
| `user_id` | UUID | FK → users.id | Actor (NULL for system) |
| `institution_id` | UUID | FK → institutions.id | Institution |
| `action` | VARCHAR(100) | NOT NULL | Action type |
| `resource_type` | VARCHAR(50) | NULL | Affected resource |
| `resource_id` | UUID | NULL | Affected resource ID |
| `ip_address` | INET | NULL | Client IP |
| `user_agent` | TEXT | NULL | Browser/client info |
| `details` | JSONB | NULL | Additional context |
| `severity` | ENUM | DEFAULT 'info' | info, warning, error, critical |
| `created_at` | TIMESTAMP | DEFAULT NOW() | Event time |

**Indexes:** `user_id`, `action`, `created_at`, `severity`

---

### `active_tokens`
Current valid session tokens (for revocation).

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Token record ID |
| `user_id` | UUID | FK → users.id, NOT NULL | User |
| `jti` | VARCHAR(255) | UNIQUE, NOT NULL | JWT ID |
| `issued_at` | TIMESTAMP | NOT NULL | Token issued |
| `expires_at` | TIMESTAMP | NOT NULL | Token expiry |
| `is_revoked` | BOOLEAN | DEFAULT FALSE | Revocation status |
| `revoked_at` | TIMESTAMP | NULL | Revocation time |
| `ip_address` | INET | NULL | Issuing IP |
| `device_fingerprint` | VARCHAR(255) | NULL | Device identifier |

**Indexes:** `user_id`, `jti`, `expires_at`, `is_revoked`

---

## Assignments & Deadlines

### `assignments`
Student assignments and deadlines.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Assignment ID |
| `title` | VARCHAR(255) | NOT NULL | Assignment name |
| `description` | TEXT | NULL | Details |
| `teacher_id` | UUID | FK → users.id | Assigning teacher |
| `institution_id` | UUID | FK → institutions.id | Institution |
| `subject_id` | UUID | FK → subjects.id | Related subject |
| `due_date` | TIMESTAMP | NOT NULL | Deadline |
| `max_points` | INTEGER | NULL | Maximum score |
| `status` | ENUM | DEFAULT 'active' | active, completed, cancelled |
| `created_at` | TIMESTAMP | DEFAULT NOW() | Creation |

---

### `user_assignments`
Assignment instances per student.

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | UUID | PRIMARY KEY | Record ID |
| `assignment_id` | UUID | FK → assignments.id | Assignment |
| `user_id` | UUID | FK → users.id | Student |
| `status` | ENUM | DEFAULT 'pending' | pending, in_progress, submitted, graded |
| `score` | DECIMAL(5,2) | NULL | Earned points |
| `submitted_at` | TIMESTAMP | NULL | Submission time |
| `graded_at` | TIMESTAMP | NULL | Grading time |
| `notes` | TEXT | NULL | Feedback notes |

**Indexes:** `user_id`, `assignment_id`, `status`, `due_date`

---

## Entity Relationship Diagram

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  institutions   │◄────┤     users       │◄────┤  user_progress  │
└────────┬────────┘     └────────┬────────┘     └─────────────────┘
         │                       │
         │         ┌─────────────┼─────────────┐
         │         │             │             │
         ▼         ▼             ▼             ▼
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│vault_configs    │     │    sessions    │     │security_logs    │
│api_endpoints    │     │session_messages│     │active_tokens    │
└─────────────────┘     └────────┬────────┘     └─────────────────┘
                                  │
         ┌────────────────────────┼────────────────────────┐
         │                        │                        │
         ▼                        ▼                        ▼
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│    subjects     │◄────┤    resources    │     │  assignments    │
│     topics      │     │ resource_tags   │     │user_assignments │
└─────────────────┘     └─────────────────┘     └─────────────────┘
```

---

## Key Relationships

- **users** ↔ **institutions**: Many-to-one
- **users** ↔ **sessions**: One-to-many
- **sessions** ↔ **session_messages**: One-to-many
- **users** ↔ **user_progress**: One-to-many
- **subjects** ↔ **topics**: One-to-many
- **resources** ↔ **subjects**: Many-to-one
- **resources** ↔ **resource_tags**: Many-to-many
- **users** ↔ **assignments**: Many-to-many via `user_assignments`
- **institutions** ↔ **vault_configurations**: One-to-one
- **institutions** ↔ **api_endpoints**: One-to-many

---

## Indexes Summary

### Performance Critical Indexes
```sql
-- User lookups
CREATE INDEX idx_users_auth0_id ON users(auth0_id);
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_role_status ON users(role, status);

-- Session queries
CREATE INDEX idx_sessions_user_date ON sessions(user_id, started_at DESC);
CREATE INDEX idx_sessions_status ON sessions(status) WHERE status = 'active';

-- Message retrieval
CREATE INDEX idx_messages_session_seq ON session_messages(session_id, created_at);

-- Progress analytics
CREATE INDEX idx_progress_user_subject ON user_progress(user_id, subject_id);

-- Resource discovery
CREATE INDEX idx_resources_featured ON resources(is_featured, subject_id) 
    WHERE is_featured = TRUE AND status = 'published';
CREATE INDEX idx_resources_search ON resources 
    USING gin(to_tsvector('english', title || ' ' || COALESCE(description, '')));

-- Security audit
CREATE INDEX idx_audit_user_time ON security_audit_logs(user_id, created_at DESC);
CREATE INDEX idx_audit_action ON security_audit_logs(action, created_at);
```

---

## Sample Queries

### Student Dashboard Data
```sql
-- Get student's progress across all subjects
SELECT s.name, s.color, p.completion_percentage, p.proficiency_score
FROM user_progress p
JOIN subjects s ON p.subject_id = s.id
WHERE p.user_id = :user_id
ORDER BY p.last_session_at DESC;

-- Recent sessions with accuracy
SELECT title, subject_id, accuracy_score, started_at, duration_minutes
FROM sessions
WHERE user_id = :user_id AND status = 'completed'
ORDER BY started_at DESC
LIMIT 10;
```

### Teacher Analytics
```sql
-- Class engagement metrics
SELECT DATE(date) as day, 
       SUM(sessions_count) as total_sessions,
       SUM(study_minutes) as total_minutes,
       AVG(cognitive_load_score) as avg_difficulty
FROM engagement_metrics
WHERE institution_id = :institution_id
  AND date >= CURRENT_DATE - INTERVAL '7 days'
GROUP BY DATE(date)
ORDER BY day;

-- Students needing attention (low engagement)
SELECT u.id, u.first_name, u.last_name, 
       COALESCE(SUM(m.sessions_count), 0) as sessions_last_week
FROM users u
LEFT JOIN engagement_metrics m ON u.id = m.user_id 
    AND m.date >= CURRENT_DATE - INTERVAL '7 days'
WHERE u.role = 'student' AND u.institution_id = :institution_id
GROUP BY u.id
HAVING COALESCE(SUM(m.sessions_count), 0) < 2;
```

---

## Migration Notes

1. **Auth0 Integration**: The `auth0_id` field links to external Auth0 user records
2. **Encryption**: Sensitive fields marked `*_encrypted` use AES-256-GCM
3. **Soft Deletes**: Use `status` fields rather than hard deletes
4. **Time Zones**: All timestamps stored in UTC, convert at application layer
5. **Partitioning**: Consider partitioning `session_messages` and `security_audit_logs` by date for large deployments
