### Issue Summary 

**Duration of Outage**: From 18th August 2024 10:00 UTC to 8:00 UTC, it lasted for 1 hour and 30 minutes.

**Impact**: Users were unable to add, delete or read posts. Almost 95% of users impacted by the service disruption. All GET POST DELETE requests resulted in a 500 Internal Server Error at the server.

**Root Cause**: The database outage caused a complete downtime in the Posts service.


### Timeline

- **08:05** - Issue detected by users.

- **08:10** - Engineering team informed with the issue via the on-call alert system.

- **08:12** - The engineering team start checking services containers.

- **08:30** - Reviewing error logs to check where the error might be coming from.

- **09:00** - The team discovered that the issue was related to the database that was down

- **09:05** - Database team was alerted and joined the investigation

- **09:10** - The team doing a temporary fix by running new temporary container using database's backups .

- **09:40** - discover the issues in the old container and then fix it.

- **10:00** - Service was restored fully, and the application behaved normally again.

### Root Cause and Resolution

**Root Cause**: Due to a recent code change, which introduced misconfiguration in one of the database queries, this triggered an error overloaded the database, resulting in a failure.

**Resolution**: The issue was resolved by first running a temporary container using backups of the database. After identifying and fixing the misconfiguration in the old container, the original setup was restored, and the service returned to normal.


### Root Cause and Resolution:

Such a code review process should be in place that any change in the code, especially relating to critical integrations, is checked thoroughly for any misconfiguration or error before deployment into the production environment.

Improved Testing and Quality Assurance: Introduce complete testing procedures, including integration testing and strong QA checks, to help identify any possible problems before they ever reach a live system. It shall include extensive testing of API integrations to make sure that they are working as expected and configured
