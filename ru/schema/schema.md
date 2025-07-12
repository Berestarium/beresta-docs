# notebook

| Column name | Type         | Required? |
|-------------|--------------|-----------|
| id          | uuid         | +         |
| name        | varchar(255) | -         |
| metadata    | jsonb        | +         |

# cells

| Column name | Type        | Required | Other Constraints        |
|-------------|-------------|----------|--------------------------|
| id          | uuid        | true     | primary key              |
| parent_id   | uuid        | false    | references cells (id)    |
| notebook_id | uuid        | true     | references notebook (id) |
| type        | varchar(16) | true     |                          |
| source      | text        | false    |                          |
| metadata    | jsonb       | false    |                          |
| position    | integer     | true     |                          |
| created_at  | timestamp   | true     |                          |
| updated_at  | timestamp   | true     |                          |
| version     | integer     | true     |                          |
| is_deleted  | boolean     |          |                          |

# users

| Column name | Type | Required |
|-------------|------|----------|
| id          | uuid | true     |

// todo cells_history in future
