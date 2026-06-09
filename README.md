# GeoServer + PostGIS Docker Stack

GeoServer and PostGIS infrastructure optimized for VPS deployment with PgBouncer connection pooling, resource limits, and automated backups.

## Stack
- **GeoServer:** `2.28.4` (Host port: `8080`)
- **PostGIS:** `16-3.4` (PostgreSQL 16 & PostGIS 3.4)
- **PgBouncer:** `1.25.1` (Host port: `5432`, transaction mode)

## Execution Instructions

1. **Initial Setup**:
   Copy the environment variables file and initialize the PgBouncer authentication file:
   ```bash
   cp .env.example .env  # If applicable
   mkdir -p pgbouncer && touch pgbouncer/userlist.txt
   ```

2. **Start the Stack**:
   ```bash
   docker compose up -d
   ```

3. **Synchronize PgBouncer Credentials** (Required on first install or when changing passwords):
   ```bash
   bash sync_pgbouncer_auth.sh
   ```

4. **Manual Backups**:
   ```bash
   bash scripts/backup_dbs.sh
   ```
