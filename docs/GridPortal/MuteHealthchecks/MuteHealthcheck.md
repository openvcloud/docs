## Mute / Un-mute Health checks

### Use case
Some health-checks need considerable time to be solved.  for example when a physical actions is required or when we understand it's a bug and it will be fixed later (e.g. false positive alarm).

### Integration with JIRA

#### Mute Health-check
When muting a health check, an issue will be created in JIRA on the configured project and the user will be required to add the following information:
- *Summary* : the title of the issue
- *Description*: detailed description of the issue
- *Priority*: priority of the issue
- *Impact*: (if it is configured in the grid settings)
- *System*: (if it is configured in the grid settings)

#### Un-mute Health-check
- a comment will be added to the related issue to report the health-check is un-muted

#### Configration
to enable the integration with jira, add the following section under ```environment.settings``` section in the system-config configmap:
```yml
jira:
    host: <JIRA hostname>
    username: <JIRA username>
    token: <JIRA API token>
    project: <Project>
```
to configure *Impact* or *System* custom fields add this to the above configrations, for example:
```yml
    fields:
    - name: Impact
      options:
      - Extensive / Widespread
      - Significant / Large
      - Moderate / Limited
      - Minor / Localized 
```
