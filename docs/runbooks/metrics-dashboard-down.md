# Runbook - Metrics Dashboard Down

## Purpose

This runbook provides response steps for a metrics dashboard outage detected by a monitoring platform.

The metrics dashboard provides visibility into system health, including CPU, memory, disk, container status, and network activity. If the metrics dashboard is unavailable, core services may still be running, but operational visibility may be reduced.

## Alert

**Metrics Dashboard is DOWN**

## Severity

**Warning**

## Affected System

| Item | Value |
|---|---|
| Service | Metrics dashboard |
| Host | Network utility server |
| Host IP | Internal network address |
| Dashboard URL | Internal metrics dashboard URL |
| Deployment type | Containerized service |
| Alert destination | Private alert channel |
| Monitoring platform | Uptime monitoring system |

## Impact

If this alert fires:

- The metrics dashboard may be unavailable.
- System performance visibility may be reduced.
- CPU, memory, disk, and network metrics may not be visible.
- Core services may still be functioning normally.

This is usually a **monitoring visibility issue**, not a full network outage.

## First Checks

1. Open the metrics dashboard in a browser.

   Example:

   ```
   http://<internal-server-ip>:<metrics-port>
   ```

   Expected if healthy:

   ```
   Metrics dashboard loads successfully.
   ```

   Expected if down:

   ```
   Browser shows connection refused, timeout, or network error.
   ```

2. Open the monitoring platform.

   Example:

   ```
   http://<internal-server-ip>:<monitoring-port>
   ```

3. Confirm the monitor status.

   ```
   Metrics Dashboard: Down
   ```

4. SSH into the network utility server from an admin workstation.

   ```
   ssh <admin-user>@<internal-server-ip>
   ```

5. Check running containers.

   ```
   docker ps
   ```

   Expected healthy result:

   ```
   Monitoring container is running.
   Metrics dashboard container is running.
   ```

6. If the metrics dashboard container is missing, move into the metrics dashboard container directory.

   ```
   cd ~/containers/<metrics-dashboard>
   ```

7. Check compose status.

   ```
   docker compose ps
   ```

   Expected healthy result:

   ```
   Metrics dashboard container is running.
   ```

## Recovery Steps

1. Start or restart the metrics dashboard container.

   ```
   docker compose up -d
   ```

2. Confirm the container is running.

   ```
   docker ps
   ```

   Expected:

   ```
   Monitoring container is running.
   Metrics dashboard container is running.
   ```

3. Check the local compose status.

   ```
   docker compose ps
   ```

   Expected:

   ```
   Metrics dashboard container is running.
   ```

4. Reopen the metrics dashboard in a browser.

   ```
   http://<internal-server-ip>:<metrics-port>
   ```

   Expected:

   ```
   Metrics dashboard loads successfully.
   ```

## Validation

After recovery, confirm:

1. The monitoring platform shows the monitor as Up.

   ```
   Metrics Dashboard: Up
   ```

2. The private alert channel receives a recovery notification.

3. Browser access to the metrics dashboard works.

   ```
   http://<internal-server-ip>:<metrics-port>
   ```

4. Docker shows the metrics dashboard container running.

   ```
   docker ps
   ```

Expected final status:

```
Metrics Dashboard monitor is Up.
Metrics dashboard loads successfully.
Recovery notification received.
```

## Escalation Steps

If the metrics dashboard does not start, check the container runtime service.

1. Check Docker service health.

   ```
   sudo systemctl status docker --no-pager
   ```

2. If Docker is not running, restart Docker.

   ```
   sudo systemctl restart docker
   ```

3. Return to the metrics dashboard directory.

   ```
   cd ~/containers/<metrics-dashboard>
   ```

4. Try starting the service again.

   ```
   docker compose up -d
   ```

5. Check recent container logs.

   ```
   docker compose logs --tail=50
   ```

Look for errors related to:

- Port binding conflicts
- Permission issues
- Container restart loops
- Missing compose files
- Volume or mount errors
- Disk space issues

6. Check disk space.

   ```
   df -h
   ```

7. Check memory.

   ```
   free -h
   ```

## Admin / Root Notes

Docker commands may not require `sudo` if the admin user is a member of the Docker group.

```
docker ps
docker compose ps
docker compose up -d
docker compose logs --tail=50
```

System service commands require `sudo` because they manage operating system services.

```
sudo systemctl status docker --no-pager
sudo systemctl restart docker
```

## Do Not

- Do not reboot the server as the first recovery step.
- Do not delete the container directory.
- Do not remove Docker volumes unless intentionally restoring from backup.
- Do not expose the metrics dashboard to the public internet.
- Do not paste alert webhook URLs, tokens, or secrets into public documentation.

## Known Good Validation

This alert path can be validated with a controlled outage test.

Test action:

```
cd ~/containers/<metrics-dashboard>
docker compose down
```

Expected result:

```
Metrics dashboard becomes unavailable.
Monitoring platform detects the outage.
Private alert channel receives a DOWN alert.
```

Recovery action:

```
docker compose up -d
```

Expected result:

```
Metrics dashboard becomes available again.
Monitoring platform detects recovery.
Private alert channel receives a recovery alert.
```

## Documentation Notes

After resolving a metrics dashboard alert, record:

| Field | Notes |
|---|---|
| Date/time | When the alert occurred |
| Alert name | Metrics Dashboard |
| Status | Down / Recovered |
| Cause | Unknown, container stopped, Docker issue, reboot, resource issue, etc. |
| Recovery action | Example: `docker compose up -d` |
| Validation | Monitor Up, dashboard loads, recovery alert received |
| Follow-up needed | Yes / No |

## Final Status

Metrics Dashboard Down runbook created. Safe outage and recovery workflow documented. Private alert notifications validated.
