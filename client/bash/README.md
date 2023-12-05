# Nextflow Tower API Bash client

## Overview

This is a Bash client script for accessing Nextflow Tower API service.

The script uses cURL underneath for making all REST calls.

## Usage

```shell
# Make sure the script has executable rights
$ chmod u+x 

# Print the list of operations available on the service
$ ./ -h

# Print the service description
$ ./ --about

# Print detailed information about specific operation
$ ./ <operationId> -h

# Make GET request
./ --host http://<hostname>:<port> --accept xml <operationId> <queryParam1>=<value1> <header_key1>:<header_value2>

# Make GET request using arbitrary curl options (must be passed before <operationId>) to an SSL service using username:password
 -k -sS --tlsv1.2 --host https://<hostname> -u <user>:<password> --accept xml <operationId> <queryParam1>=<value1> <header_key1>:<header_value2>

# Make POST request
$ echo '<body_content>' |  --host <hostname> --content-type json <operationId> -

# Make POST request with simple JSON content, e.g.:
# {
#   "key1": "value1",
#   "key2": "value2",
#   "key3": 23
# }
$ echo '<body_content>' |  --host <hostname> --content-type json <operationId> key1==value1 key2=value2 key3:=23 -

# Make POST request with form data
$  --host <hostname> <operationId> key1:=value1 key2:=value2 key3:=23

# Preview the cURL command without actually executing it
$  --host http://<hostname>:<port> --dry-run <operationid>

```

## Docker image

You can easily create a Docker image containing a preconfigured environment
for using the REST Bash client including working autocompletion and short
welcome message with basic instructions, using the generated Dockerfile:

```shell
docker build -t my-rest-client .
docker run -it my-rest-client
```

By default you will be logged into a Zsh environment which has much more
advanced auto completion, but you can switch to Bash, where basic autocompletion
is also available.

## Shell completion

### Bash

The generated bash-completion script can be either directly loaded to the current Bash session using:

```shell
source .bash-completion
```

Alternatively, the script can be copied to the `/etc/bash-completion.d` (or on OSX with Homebrew to `/usr/local/etc/bash-completion.d`):

```shell
sudo cp .bash-completion /etc/bash-completion.d/
```

#### OS X

On OSX you might need to install bash-completion using Homebrew:

```shell
brew install bash-completion
```

and add the following to the `~/.bashrc`:

```shell
if [ -f $(brew --prefix)/etc/bash_completion ]; then
  . $(brew --prefix)/etc/bash_completion
fi
```

### Zsh

In Zsh, the generated `_` Zsh completion file must be copied to one of the folders under `$FPATH` variable.

## Documentation for API Endpoints

All URIs are relative to **

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*DefaultApi* | [**addLabelsToActions**](docs/DefaultApi.md#addlabelstoactions) | **POST** /actions/labels/add | Add labels to actions
*DefaultApi* | [**addLabelsToPipelines**](docs/DefaultApi.md#addlabelstopipelines) | **POST** /pipelines/labels/add | Add labels to pipelines
*DefaultApi* | [**addLabelsToWorkflows**](docs/DefaultApi.md#addlabelstoworkflows) | **POST** /workflow/labels/add | Add labels to workflows
*DefaultApi* | [**applyLabelsToActions**](docs/DefaultApi.md#applylabelstoactions) | **POST** /actions/labels/apply | Apply labels to actions
*DefaultApi* | [**applyLabelsToPipelines**](docs/DefaultApi.md#applylabelstopipelines) | **POST** /pipelines/labels/apply | Apply labels to pipelines
*DefaultApi* | [**applyLabelsToWorkflows**](docs/DefaultApi.md#applylabelstoworkflows) | **POST** /workflow/labels/apply | Apply labels to workflows
*DefaultApi* | [**cancelWorkflow**](docs/DefaultApi.md#cancelworkflow) | **POST** /workflow/{workflowId}/cancel | Cancel workflow
*DefaultApi* | [**createAction**](docs/DefaultApi.md#createaction) | **POST** /actions | Create action
*DefaultApi* | [**createAvatar**](docs/DefaultApi.md#createavatar) | **POST** /avatars | Create the avatar image
*DefaultApi* | [**createComputeEnv**](docs/DefaultApi.md#createcomputeenv) | **POST** /compute-envs | Create compute environment
*DefaultApi* | [**createCredentials**](docs/DefaultApi.md#createcredentials) | **POST** /credentials | Create credentials
*DefaultApi* | [**createDataset**](docs/DefaultApi.md#createdataset) | **POST** /workspaces/{workspaceId}/datasets | Create dataset
*DefaultApi* | [**createLabel**](docs/DefaultApi.md#createlabel) | **POST** /labels | Create label
*DefaultApi* | [**createOrganization**](docs/DefaultApi.md#createorganization) | **POST** /orgs | Create organization
*DefaultApi* | [**createOrganizationMember**](docs/DefaultApi.md#createorganizationmember) | **PUT** /orgs/{orgId}/members/add | Add organization member
*DefaultApi* | [**createOrganizationTeam**](docs/DefaultApi.md#createorganizationteam) | **POST** /orgs/{orgId}/teams | Create team
*DefaultApi* | [**createOrganizationTeamMember**](docs/DefaultApi.md#createorganizationteammember) | **POST** /orgs/{orgId}/teams/{teamId}/members | Create team member
*DefaultApi* | [**createPipeline**](docs/DefaultApi.md#createpipeline) | **POST** /pipelines | Create pipeline
*DefaultApi* | [**createPipelineSecret**](docs/DefaultApi.md#createpipelinesecret) | **POST** /pipeline-secrets | Create pipeline secret
*DefaultApi* | [**createToken**](docs/DefaultApi.md#createtoken) | **POST** /tokens | Create an API token
*DefaultApi* | [**createTrace**](docs/DefaultApi.md#createtrace) | **POST** /trace/create | Create a new Workflow execution trace
*DefaultApi* | [**createWorkflowLaunch**](docs/DefaultApi.md#createworkflowlaunch) | **POST** /workflow/launch | Launch workflow
*DefaultApi* | [**createWorkflowStar**](docs/DefaultApi.md#createworkflowstar) | **POST** /workflow/{workflowId}/star | Star workflow
*DefaultApi* | [**createWorkspace**](docs/DefaultApi.md#createworkspace) | **POST** /orgs/{orgId}/workspaces | Create workspace
*DefaultApi* | [**createWorkspaceParticipant**](docs/DefaultApi.md#createworkspaceparticipant) | **PUT** /orgs/{orgId}/workspaces/{workspaceId}/participants/add | Create workspace participant
*DefaultApi* | [**deleteAction**](docs/DefaultApi.md#deleteaction) | **DELETE** /actions/{actionId} | Delete action
*DefaultApi* | [**deleteAllTokens**](docs/DefaultApi.md#deletealltokens) | **DELETE** /tokens/delete-all | Delete all user API tokens
*DefaultApi* | [**deleteComputeEnv**](docs/DefaultApi.md#deletecomputeenv) | **DELETE** /compute-envs/{computeEnvId} | Delete compute environment
*DefaultApi* | [**deleteCredentials**](docs/DefaultApi.md#deletecredentials) | **DELETE** /credentials/{credentialsId} | Delete credentials
*DefaultApi* | [**deleteDataset**](docs/DefaultApi.md#deletedataset) | **DELETE** /workspaces/{workspaceId}/datasets/{datasetId} | Delete dataset
*DefaultApi* | [**deleteLabel**](docs/DefaultApi.md#deletelabel) | **DELETE** /labels/{labelId} | Delete label
*DefaultApi* | [**deleteOrganization**](docs/DefaultApi.md#deleteorganization) | **DELETE** /orgs/{orgId} | Delete organization
*DefaultApi* | [**deleteOrganizationMember**](docs/DefaultApi.md#deleteorganizationmember) | **DELETE** /orgs/{orgId}/members/{memberId} | Delete member
*DefaultApi* | [**deleteOrganizationTeam**](docs/DefaultApi.md#deleteorganizationteam) | **DELETE** /orgs/{orgId}/teams/{teamId} | Delete team
*DefaultApi* | [**deleteOrganizationTeamMember**](docs/DefaultApi.md#deleteorganizationteammember) | **DELETE** /orgs/{orgId}/teams/{teamId}/members/{memberId}/delete | Delete team member
*DefaultApi* | [**deletePipeline**](docs/DefaultApi.md#deletepipeline) | **DELETE** /pipelines/{pipelineId} | Delete pipeline
*DefaultApi* | [**deletePipelineSecret**](docs/DefaultApi.md#deletepipelinesecret) | **DELETE** /pipeline-secrets/{secretId} | Delete secret
*DefaultApi* | [**deleteToken**](docs/DefaultApi.md#deletetoken) | **DELETE** /tokens/{tokenId} | Delete an API token
*DefaultApi* | [**deleteUser**](docs/DefaultApi.md#deleteuser) | **DELETE** /users/{userId} | Delete a user entity
*DefaultApi* | [**deleteWorkflow**](docs/DefaultApi.md#deleteworkflow) | **DELETE** /workflow/{workflowId} | Delete the Workflow entity with the given ID
*DefaultApi* | [**deleteWorkflowMany**](docs/DefaultApi.md#deleteworkflowmany) | **POST** /workflow/delete | Delete workflows
*DefaultApi* | [**deleteWorkflowStar**](docs/DefaultApi.md#deleteworkflowstar) | **DELETE** /workflow/{workflowId}/star | Unstar workflow
*DefaultApi* | [**deleteWorkspace**](docs/DefaultApi.md#deleteworkspace) | **DELETE** /orgs/{orgId}/workspaces/{workspaceId} | Delete workspace
*DefaultApi* | [**deleteWorkspaceParticipant**](docs/DefaultApi.md#deleteworkspaceparticipant) | **DELETE** /orgs/{orgId}/workspaces/{workspaceId}/participants/{participantId} | Delete workspace participant
*DefaultApi* | [**describeAction**](docs/DefaultApi.md#describeaction) | **GET** /actions/{actionId} | Describe action
*DefaultApi* | [**describeComputeEnv**](docs/DefaultApi.md#describecomputeenv) | **GET** /compute-envs/{computeEnvId} | Describe compute environment
*DefaultApi* | [**describeCredentials**](docs/DefaultApi.md#describecredentials) | **GET** /credentials/{credentialsId} | Describe credentials
*DefaultApi* | [**describeDataset**](docs/DefaultApi.md#describedataset) | **GET** /workspaces/{workspaceId}/datasets/{datasetId}/metadata | Describe dataset
*DefaultApi* | [**describeLaunch**](docs/DefaultApi.md#describelaunch) | **GET** /launch/{launchId} | Describe Launch record
*DefaultApi* | [**describeOrganization**](docs/DefaultApi.md#describeorganization) | **GET** /orgs/{orgId} | Describe organization
*DefaultApi* | [**describeOrganizationTeam**](docs/DefaultApi.md#describeorganizationteam) | **GET** /orgs/{orgId}/teams/{teamId} | Describe team
*DefaultApi* | [**describePipeline**](docs/DefaultApi.md#describepipeline) | **GET** /pipelines/{pipelineId} | Describe pipeline
*DefaultApi* | [**describePipelineLaunch**](docs/DefaultApi.md#describepipelinelaunch) | **GET** /pipelines/{pipelineId}/launch | Describe pipeline launch
*DefaultApi* | [**describePipelineRepository**](docs/DefaultApi.md#describepipelinerepository) | **GET** /pipelines/info | Describe remote pipeline repository
*DefaultApi* | [**describePipelineSchema**](docs/DefaultApi.md#describepipelineschema) | **GET** /pipelines/{pipelineId}/schema | Describe pipeline schema
*DefaultApi* | [**describePipelineSecret**](docs/DefaultApi.md#describepipelinesecret) | **GET** /pipeline-secrets/{secretId} | Describe pipeline secret
*DefaultApi* | [**describePlatform**](docs/DefaultApi.md#describeplatform) | **GET** /platforms/{platformId} | Describe platform
*DefaultApi* | [**describeUser**](docs/DefaultApi.md#describeuser) | **GET** /users/{userId} | Describe a user entity
*DefaultApi* | [**describeWorkflow**](docs/DefaultApi.md#describeworkflow) | **GET** /workflow/{workflowId} | Describe workflow
*DefaultApi* | [**describeWorkflowLaunch**](docs/DefaultApi.md#describeworkflowlaunch) | **GET** /workflow/{workflowId}/launch | Describe workflow launch
*DefaultApi* | [**describeWorkflowMetrics**](docs/DefaultApi.md#describeworkflowmetrics) | **GET** /workflow/{workflowId}/metrics | Get the execution metrics for the given Workflow ID
*DefaultApi* | [**describeWorkflowProgress**](docs/DefaultApi.md#describeworkflowprogress) | **GET** /workflow/{workflowId}/progress | Retrieve the execution progress for the given Workflow ID
*DefaultApi* | [**describeWorkflowStar**](docs/DefaultApi.md#describeworkflowstar) | **GET** /workflow/{workflowId}/star | Check workflow star status
*DefaultApi* | [**describeWorkflowTask**](docs/DefaultApi.md#describeworkflowtask) | **GET** /workflow/{workflowId}/task/{taskId} | Describe a task entity with the given ID
*DefaultApi* | [**describeWorkspace**](docs/DefaultApi.md#describeworkspace) | **GET** /orgs/{orgId}/workspaces/{workspaceId} | Describe workspace
*DefaultApi* | [**downloadAvatar**](docs/DefaultApi.md#downloadavatar) | **GET** /avatars/{avatarId} | Download the avatar image
*DefaultApi* | [**downloadDataset**](docs/DefaultApi.md#downloaddataset) | **GET** /workspaces/{workspaceId}/datasets/{datasetId}/v/{version}/n/{fileName} | Download dataset content
*DefaultApi* | [**downloadWorkflowLog**](docs/DefaultApi.md#downloadworkflowlog) | **GET** /workflow/{workflowId}/download | Download workflow files
*DefaultApi* | [**downloadWorkflowTaskLog**](docs/DefaultApi.md#downloadworkflowtasklog) | **GET** /workflow/{workflowId}/download/{taskId} | Download workflow task files
*DefaultApi* | [**gaRunCancel**](docs/DefaultApi.md#garuncancel) | **POST** /ga4gh/wes/v1/runs/{run_id}/cancel | GA4GH cancel a run
*DefaultApi* | [**gaRunCreate**](docs/DefaultApi.md#garuncreate) | **POST** /ga4gh/wes/v1/runs | GA4GH create a new run
*DefaultApi* | [**gaRunDescribe**](docs/DefaultApi.md#garundescribe) | **GET** /ga4gh/wes/v1/runs/{run_id} | GA4GH describe run
*DefaultApi* | [**gaRunList**](docs/DefaultApi.md#garunlist) | **GET** /ga4gh/wes/v1/runs | GA4GH list runs
*DefaultApi* | [**gaRunStatus**](docs/DefaultApi.md#garunstatus) | **GET** /ga4gh/wes/v1/runs/{run_id}/status | GA4GH retrieve run status
*DefaultApi* | [**gaServiceInfo**](docs/DefaultApi.md#gaserviceinfo) | **GET** /ga4gh/wes/v1/service-info | GA4GH service info
*DefaultApi* | [**generateRandomWorkflowName**](docs/DefaultApi.md#generaterandomworkflowname) | **GET** /workflow/random-name | Generates a random name
*DefaultApi* | [**getWorkflowTaskLog**](docs/DefaultApi.md#getworkflowtasklog) | **GET** /workflow/{workflowId}/log/{taskId} | Get workflow task logs
*DefaultApi* | [**info**](docs/DefaultApi.md#info) | **GET** /service-info | General Tower service features and version
*DefaultApi* | [**launchAction**](docs/DefaultApi.md#launchaction) | **POST** /actions/{actionId}/launch | Trigger Tower Launch action
*DefaultApi* | [**leaveOrganization**](docs/DefaultApi.md#leaveorganization) | **DELETE** /orgs/{orgId}/members/leave | Leave organization
*DefaultApi* | [**leaveWorkspaceParticipant**](docs/DefaultApi.md#leaveworkspaceparticipant) | **DELETE** /orgs/{orgId}/workspaces/{workspaceId}/participants | Leave workspace
*DefaultApi* | [**listActionTypes**](docs/DefaultApi.md#listactiontypes) | **GET** /actions/types | List action event types
*DefaultApi* | [**listActions**](docs/DefaultApi.md#listactions) | **GET** /actions | List actions
*DefaultApi* | [**listComputeEnvs**](docs/DefaultApi.md#listcomputeenvs) | **GET** /compute-envs | List compute environments
*DefaultApi* | [**listCredentials**](docs/DefaultApi.md#listcredentials) | **GET** /credentials | List credentials
*DefaultApi* | [**listDatasetVersions**](docs/DefaultApi.md#listdatasetversions) | **GET** /workspaces/{workspaceId}/datasets/{datasetId}/versions | List all dataset versions
*DefaultApi* | [**listDatasets**](docs/DefaultApi.md#listdatasets) | **GET** /workspaces/{workspaceId}/datasets | List available datasets
*DefaultApi* | [**listLabels**](docs/DefaultApi.md#listlabels) | **GET** /labels | List labels
*DefaultApi* | [**listLaunchDatasetVersions**](docs/DefaultApi.md#listlaunchdatasetversions) | **GET** /launch/{launchId}/datasets | Describe launch datasets
*DefaultApi* | [**listOrganizationCollaborators**](docs/DefaultApi.md#listorganizationcollaborators) | **GET** /orgs/{orgId}/collaborators | List organization collaborators
*DefaultApi* | [**listOrganizationMembers**](docs/DefaultApi.md#listorganizationmembers) | **GET** /orgs/{orgId}/members | List organization members
*DefaultApi* | [**listOrganizationTeamMembers**](docs/DefaultApi.md#listorganizationteammembers) | **GET** /orgs/{orgId}/teams/{teamId}/members | List team members
*DefaultApi* | [**listOrganizationTeams**](docs/DefaultApi.md#listorganizationteams) | **GET** /orgs/{orgId}/teams | List organization teams
*DefaultApi* | [**listOrganizations**](docs/DefaultApi.md#listorganizations) | **GET** /orgs | List organizations
*DefaultApi* | [**listPipelineRepositories**](docs/DefaultApi.md#listpipelinerepositories) | **GET** /pipelines/repositories | List user pipeline repositories
*DefaultApi* | [**listPipelineSecrets**](docs/DefaultApi.md#listpipelinesecrets) | **GET** /pipeline-secrets | List pipeline secrets
*DefaultApi* | [**listPipelines**](docs/DefaultApi.md#listpipelines) | **GET** /pipelines | List Tower pipelines
*DefaultApi* | [**listPlatformRegions**](docs/DefaultApi.md#listplatformregions) | **GET** /platforms/{platformId}/regions | List platform regions
*DefaultApi* | [**listPlatforms**](docs/DefaultApi.md#listplatforms) | **GET** /platforms | List platforms
*DefaultApi* | [**listWorkflowTasks**](docs/DefaultApi.md#listworkflowtasks) | **GET** /workflow/{workflowId}/tasks | List the tasks for the given Workflow ID and filter parameters
*DefaultApi* | [**listWorkflows**](docs/DefaultApi.md#listworkflows) | **GET** /workflow | List workflows
*DefaultApi* | [**listWorkspaceDatasetVersions**](docs/DefaultApi.md#listworkspacedatasetversions) | **GET** /workspaces/{workspaceId}/datasets/versions | List latest dataset versions
*DefaultApi* | [**listWorkspaceParticipants**](docs/DefaultApi.md#listworkspaceparticipants) | **GET** /orgs/{orgId}/workspaces/{workspaceId}/participants | List workspace participants
*DefaultApi* | [**listWorkspaces**](docs/DefaultApi.md#listworkspaces) | **GET** /orgs/{orgId}/workspaces | List organization workspaces
*DefaultApi* | [**listWorkspacesByTeam**](docs/DefaultApi.md#listworkspacesbyteam) | **GET** /orgs/{orgId}/teams/{teamId}/workspaces | List team workspaces
*DefaultApi* | [**listWorkspacesUser**](docs/DefaultApi.md#listworkspacesuser) | **GET** /user/{userId}/workspaces | List user workspaces and organizations
*DefaultApi* | [**pauseAction**](docs/DefaultApi.md#pauseaction) | **POST** /actions/{actionId}/pause | Pause or resume action
*DefaultApi* | [**removeLabelsFromActions**](docs/DefaultApi.md#removelabelsfromactions) | **POST** /actions/labels/remove | Remove labels from actions
*DefaultApi* | [**removeLabelsFromPipelines**](docs/DefaultApi.md#removelabelsfrompipelines) | **POST** /pipelines/labels/remove | Remove labels from pipelines
*DefaultApi* | [**removeLabelsFromWorkflows**](docs/DefaultApi.md#removelabelsfromworkflows) | **POST** /workflow/labels/remove | Remove labels from workflows
*DefaultApi* | [**tokenList**](docs/DefaultApi.md#tokenlist) | **GET** /tokens | List all available API tokens
*DefaultApi* | [**updateAction**](docs/DefaultApi.md#updateaction) | **PUT** /actions/{actionId} | Update action
*DefaultApi* | [**updateComputeEnv**](docs/DefaultApi.md#updatecomputeenv) | **PUT** /compute-envs/{computeEnvId} | Update compute environment
*DefaultApi* | [**updateComputeEnvPrimary**](docs/DefaultApi.md#updatecomputeenvprimary) | **POST** /compute-envs/{computeEnvId}/primary | Define primary compute environment
*DefaultApi* | [**updateCredentials**](docs/DefaultApi.md#updatecredentials) | **PUT** /credentials/{credentialsId} | Update credentials
*DefaultApi* | [**updateDataset**](docs/DefaultApi.md#updatedataset) | **PUT** /workspaces/{workspaceId}/datasets/{datasetId} | Update dataset
*DefaultApi* | [**updateLabel**](docs/DefaultApi.md#updatelabel) | **PUT** /labels/{labelId} | Update label
*DefaultApi* | [**updateOrganization**](docs/DefaultApi.md#updateorganization) | **PUT** /orgs/{orgId} | Update organization
*DefaultApi* | [**updateOrganizationMemberRole**](docs/DefaultApi.md#updateorganizationmemberrole) | **PUT** /orgs/{orgId}/members/{memberId}/role | Update member role
*DefaultApi* | [**updateOrganizationTeam**](docs/DefaultApi.md#updateorganizationteam) | **PUT** /orgs/{orgId}/teams/{teamId} | Update team
*DefaultApi* | [**updatePipeline**](docs/DefaultApi.md#updatepipeline) | **PUT** /pipelines/{pipelineId} | Update pipeline
*DefaultApi* | [**updatePipelineSecret**](docs/DefaultApi.md#updatepipelinesecret) | **PUT** /pipeline-secrets/{secretId} | Update secret
*DefaultApi* | [**updateTraceBegin**](docs/DefaultApi.md#updatetracebegin) | **PUT** /trace/{workflowId}/begin | Signal the Workflow execution has started
*DefaultApi* | [**updateTraceComplete**](docs/DefaultApi.md#updatetracecomplete) | **PUT** /trace/{workflowId}/complete | Signal the Workflow execution has completed
*DefaultApi* | [**updateTraceHeartbeat**](docs/DefaultApi.md#updatetraceheartbeat) | **PUT** /trace/{workflowId}/heartbeat | Period request to signal the execution is still on-going
*DefaultApi* | [**updateTraceProgress**](docs/DefaultApi.md#updatetraceprogress) | **PUT** /trace/{workflowId}/progress | Store one or more task executions metadata for the specified Workflow
*DefaultApi* | [**updateUser**](docs/DefaultApi.md#updateuser) | **POST** /users/{userId} | Update an user entity
*DefaultApi* | [**updateWorkspace**](docs/DefaultApi.md#updateworkspace) | **PUT** /orgs/{orgId}/workspaces/{workspaceId} | Update workspace
*DefaultApi* | [**updateWorkspaceParticipantRole**](docs/DefaultApi.md#updateworkspaceparticipantrole) | **PUT** /orgs/{orgId}/workspaces/{workspaceId}/participants/{participantId}/role | Update participant role
*DefaultApi* | [**uploadDataset**](docs/DefaultApi.md#uploaddataset) | **POST** /workspaces/{workspaceId}/datasets/{datasetId}/upload | Upload new dataset version
*DefaultApi* | [**userInfo**](docs/DefaultApi.md#userinfo) | **GET** /user-info | Describe current user
*DefaultApi* | [**validateActionName**](docs/DefaultApi.md#validateactionname) | **GET** /actions/validate | Validate action name
*DefaultApi* | [**validateComputeEnvName**](docs/DefaultApi.md#validatecomputeenvname) | **GET** /compute-envs/validate | Validate compute environment name
*DefaultApi* | [**validateCredentialsName**](docs/DefaultApi.md#validatecredentialsname) | **GET** /credentials/validate | Validate credential name
*DefaultApi* | [**validateOrganizationName**](docs/DefaultApi.md#validateorganizationname) | **GET** /orgs/validate | Validate organization name
*DefaultApi* | [**validatePipelineName**](docs/DefaultApi.md#validatepipelinename) | **GET** /pipelines/validate | Validate pipeline name
*DefaultApi* | [**validatePipelineSecretName**](docs/DefaultApi.md#validatepipelinesecretname) | **GET** /pipeline-secrets/validate | Validate secret name
*DefaultApi* | [**validateTeamName**](docs/DefaultApi.md#validateteamname) | **GET** /orgs/{orgId}/teams/validate | Validate team name
*DefaultApi* | [**validateUserName**](docs/DefaultApi.md#validateusername) | **GET** /users/validate | Check that the user name is valid
*DefaultApi* | [**validateWorkflowConstraints**](docs/DefaultApi.md#validateworkflowconstraints) | **GET** /workflow/validate | Check that the given run name of a workflow has a valid format. When the session ID is given: check that no other workflow in the system exists with the combination of both elements
*DefaultApi* | [**workflowLogs**](docs/DefaultApi.md#workflowlogs) | **GET** /workflow/{workflowId}/log | Get workflow logs
*DefaultApi* | [**workspaceValidate**](docs/DefaultApi.md#workspacevalidate) | **GET** /orgs/{orgId}/workspaces/validate | Validate workspace name


## Documentation For Models

 - [AbstractGridConfig](docs/AbstractGridConfig.md)
 - [AccessToken](docs/AccessToken.md)
 - [ActionConfigType](docs/ActionConfigType.md)
 - [ActionEventType](docs/ActionEventType.md)
 - [ActionQueryAttribute](docs/ActionQueryAttribute.md)
 - [ActionResponseDto](docs/ActionResponseDto.md)
 - [ActionSource](docs/ActionSource.md)
 - [ActionStatus](docs/ActionStatus.md)
 - [ActionTowerActionConfig](docs/ActionTowerActionConfig.md)
 - [ActionTowerActionEvent](docs/ActionTowerActionEvent.md)
 - [AddMemberRequest](docs/AddMemberRequest.md)
 - [AddMemberResponse](docs/AddMemberResponse.md)
 - [AddParticipantRequest](docs/AddParticipantRequest.md)
 - [AddParticipantResponse](docs/AddParticipantResponse.md)
 - [AddTeamMemberResponse](docs/AddTeamMemberResponse.md)
 - [AgentSecurityKeys](docs/AgentSecurityKeys.md)
 - [AltairPbsComputeConfig](docs/AltairPbsComputeConfig.md)
 - [AltairPbsComputeConfigAllOf](docs/AltairPbsComputeConfigAllOf.md)
 - [Analytics](docs/Analytics.md)
 - [AssociateActionLabelsRequest](docs/AssociateActionLabelsRequest.md)
 - [AssociatePipelineLabelsRequest](docs/AssociatePipelineLabelsRequest.md)
 - [AssociateWorkflowLabelsRequest](docs/AssociateWorkflowLabelsRequest.md)
 - [Avatar](docs/Avatar.md)
 - [AwsBatchConfig](docs/AwsBatchConfig.md)
 - [AwsBatchPlatformMetainfo](docs/AwsBatchPlatformMetainfo.md)
 - [AwsBatchPlatformMetainfoBucket](docs/AwsBatchPlatformMetainfoBucket.md)
 - [AwsBatchPlatformMetainfoEfsFileSystem](docs/AwsBatchPlatformMetainfoEfsFileSystem.md)
 - [AwsBatchPlatformMetainfoFsxFileSystem](docs/AwsBatchPlatformMetainfoFsxFileSystem.md)
 - [AwsBatchPlatformMetainfoImage](docs/AwsBatchPlatformMetainfoImage.md)
 - [AwsBatchPlatformMetainfoJobQueue](docs/AwsBatchPlatformMetainfoJobQueue.md)
 - [AwsBatchPlatformMetainfoSecurityGroup](docs/AwsBatchPlatformMetainfoSecurityGroup.md)
 - [AwsBatchPlatformMetainfoSubnet](docs/AwsBatchPlatformMetainfoSubnet.md)
 - [AwsBatchPlatformMetainfoVpc](docs/AwsBatchPlatformMetainfoVpc.md)
 - [AwsSecurityKeys](docs/AwsSecurityKeys.md)
 - [AzBatchConfig](docs/AzBatchConfig.md)
 - [AzBatchForgeConfig](docs/AzBatchForgeConfig.md)
 - [AzureReposSecurityKeys](docs/AzureReposSecurityKeys.md)
 - [AzureSecurityKeys](docs/AzureSecurityKeys.md)
 - [BitBucketSecurityKeys](docs/BitBucketSecurityKeys.md)
 - [CloudPriceModel](docs/CloudPriceModel.md)
 - [CodeCommitSecurityKeys](docs/CodeCommitSecurityKeys.md)
 - [ComputeConfig](docs/ComputeConfig.md)
 - [ComputeEnv](docs/ComputeEnv.md)
 - [ComputeEnvDbDto](docs/ComputeEnvDbDto.md)
 - [ComputeEnvQueryAttribute](docs/ComputeEnvQueryAttribute.md)
 - [ComputeEnvResponseDto](docs/ComputeEnvResponseDto.md)
 - [ComputeEnvStatus](docs/ComputeEnvStatus.md)
 - [ComputePlatform](docs/ComputePlatform.md)
 - [ComputePlatformDto](docs/ComputePlatformDto.md)
 - [ComputeRegion](docs/ComputeRegion.md)
 - [ConfigEnvVariable](docs/ConfigEnvVariable.md)
 - [ContainerRegistryKeys](docs/ContainerRegistryKeys.md)
 - [CreateAccessTokenRequest](docs/CreateAccessTokenRequest.md)
 - [CreateAccessTokenResponse](docs/CreateAccessTokenResponse.md)
 - [CreateActionRequest](docs/CreateActionRequest.md)
 - [CreateActionResponse](docs/CreateActionResponse.md)
 - [CreateAvatarResponse](docs/CreateAvatarResponse.md)
 - [CreateComputeEnvRequest](docs/CreateComputeEnvRequest.md)
 - [CreateComputeEnvResponse](docs/CreateComputeEnvResponse.md)
 - [CreateCredentialsRequest](docs/CreateCredentialsRequest.md)
 - [CreateCredentialsResponse](docs/CreateCredentialsResponse.md)
 - [CreateDatasetRequest](docs/CreateDatasetRequest.md)
 - [CreateDatasetResponse](docs/CreateDatasetResponse.md)
 - [CreateLabelRequest](docs/CreateLabelRequest.md)
 - [CreateLabelResponse](docs/CreateLabelResponse.md)
 - [CreateOrganizationRequest](docs/CreateOrganizationRequest.md)
 - [CreateOrganizationResponse](docs/CreateOrganizationResponse.md)
 - [CreatePipelineRequest](docs/CreatePipelineRequest.md)
 - [CreatePipelineResponse](docs/CreatePipelineResponse.md)
 - [CreatePipelineSecretRequest](docs/CreatePipelineSecretRequest.md)
 - [CreatePipelineSecretResponse](docs/CreatePipelineSecretResponse.md)
 - [CreateTeamMemberRequest](docs/CreateTeamMemberRequest.md)
 - [CreateTeamRequest](docs/CreateTeamRequest.md)
 - [CreateTeamResponse](docs/CreateTeamResponse.md)
 - [CreateWorkflowStarResponse](docs/CreateWorkflowStarResponse.md)
 - [CreateWorkspaceRequest](docs/CreateWorkspaceRequest.md)
 - [CreateWorkspaceResponse](docs/CreateWorkspaceResponse.md)
 - [Credentials](docs/Credentials.md)
 - [Dataset](docs/Dataset.md)
 - [DatasetVersionDbDto](docs/DatasetVersionDbDto.md)
 - [DeleteWorkflowsRequest](docs/DeleteWorkflowsRequest.md)
 - [DeleteWorkflowsResponse](docs/DeleteWorkflowsResponse.md)
 - [DescribeActionResponse](docs/DescribeActionResponse.md)
 - [DescribeComputeEnvResponse](docs/DescribeComputeEnvResponse.md)
 - [DescribeCredentialsResponse](docs/DescribeCredentialsResponse.md)
 - [DescribeDatasetResponse](docs/DescribeDatasetResponse.md)
 - [DescribeLaunchResponse](docs/DescribeLaunchResponse.md)
 - [DescribeOrganizationResponse](docs/DescribeOrganizationResponse.md)
 - [DescribePipelineInfoResponse](docs/DescribePipelineInfoResponse.md)
 - [DescribePipelineResponse](docs/DescribePipelineResponse.md)
 - [DescribePipelineSecretResponse](docs/DescribePipelineSecretResponse.md)
 - [DescribePlatformResponse](docs/DescribePlatformResponse.md)
 - [DescribeTaskResponse](docs/DescribeTaskResponse.md)
 - [DescribeTeamResponse](docs/DescribeTeamResponse.md)
 - [DescribeUserResponse](docs/DescribeUserResponse.md)
 - [DescribeWorkflowLaunchResponse](docs/DescribeWorkflowLaunchResponse.md)
 - [DescribeWorkflowResponse](docs/DescribeWorkflowResponse.md)
 - [DescribeWorkspaceResponse](docs/DescribeWorkspaceResponse.md)
 - [EksComputeConfig](docs/EksComputeConfig.md)
 - [EksComputeConfigAllOf](docs/EksComputeConfigAllOf.md)
 - [ErrorResponse](docs/ErrorResponse.md)
 - [EventType](docs/EventType.md)
 - [ForgeConfig](docs/ForgeConfig.md)
 - [GetProgressResponse](docs/GetProgressResponse.md)
 - [GetWorkflowMetricsResponse](docs/GetWorkflowMetricsResponse.md)
 - [GitHubSecurityKeys](docs/GitHubSecurityKeys.md)
 - [GitLabSecurityKeys](docs/GitLabSecurityKeys.md)
 - [GiteaSecurityKeys](docs/GiteaSecurityKeys.md)
 - [GithubActionConfig](docs/GithubActionConfig.md)
 - [GithubActionEvent](docs/GithubActionEvent.md)
 - [GkeComputeConfig](docs/GkeComputeConfig.md)
 - [GkeComputeConfigAllOf](docs/GkeComputeConfigAllOf.md)
 - [GoogleBatchConfig](docs/GoogleBatchConfig.md)
 - [GoogleLifeSciencesConfig](docs/GoogleLifeSciencesConfig.md)
 - [GooglePlatformMetainfo](docs/GooglePlatformMetainfo.md)
 - [GooglePlatformMetainfoBucket](docs/GooglePlatformMetainfoBucket.md)
 - [GooglePlatformMetainfoFilestore](docs/GooglePlatformMetainfoFilestore.md)
 - [GoogleSecurityKeys](docs/GoogleSecurityKeys.md)
 - [JobCleanupPolicy](docs/JobCleanupPolicy.md)
 - [JobInfoDto](docs/JobInfoDto.md)
 - [K8sComputeConfig](docs/K8sComputeConfig.md)
 - [K8sSecurityKeys](docs/K8sSecurityKeys.md)
 - [LabelDbDto](docs/LabelDbDto.md)
 - [LabelType](docs/LabelType.md)
 - [Launch](docs/Launch.md)
 - [LaunchActionRequest](docs/LaunchActionRequest.md)
 - [LaunchActionResponse](docs/LaunchActionResponse.md)
 - [ListAccessTokensResponse](docs/ListAccessTokensResponse.md)
 - [ListActionsResponse](docs/ListActionsResponse.md)
 - [ListActionsResponseActionInfo](docs/ListActionsResponseActionInfo.md)
 - [ListComputeEnvsResponse](docs/ListComputeEnvsResponse.md)
 - [ListComputeEnvsResponseEntry](docs/ListComputeEnvsResponseEntry.md)
 - [ListCredentialsResponse](docs/ListCredentialsResponse.md)
 - [ListDatasetVersionsResponse](docs/ListDatasetVersionsResponse.md)
 - [ListDatasetsResponse](docs/ListDatasetsResponse.md)
 - [ListEventTypesResponse](docs/ListEventTypesResponse.md)
 - [ListLabelsResponse](docs/ListLabelsResponse.md)
 - [ListMembersResponse](docs/ListMembersResponse.md)
 - [ListOrganizationsResponse](docs/ListOrganizationsResponse.md)
 - [ListParticipantsResponse](docs/ListParticipantsResponse.md)
 - [ListPipelineInfoResponse](docs/ListPipelineInfoResponse.md)
 - [ListPipelineSecretsResponse](docs/ListPipelineSecretsResponse.md)
 - [ListPipelinesResponse](docs/ListPipelinesResponse.md)
 - [ListPlatformsResponse](docs/ListPlatformsResponse.md)
 - [ListRegionsResponse](docs/ListRegionsResponse.md)
 - [ListTasksResponse](docs/ListTasksResponse.md)
 - [ListTeamResponse](docs/ListTeamResponse.md)
 - [ListWorkflowsResponse](docs/ListWorkflowsResponse.md)
 - [ListWorkflowsResponseListWorkflowsElement](docs/ListWorkflowsResponseListWorkflowsElement.md)
 - [ListWorkspacesAndOrgResponse](docs/ListWorkspacesAndOrgResponse.md)
 - [ListWorkspacesResponse](docs/ListWorkspacesResponse.md)
 - [Log](docs/Log.md)
 - [LogPage](docs/LogPage.md)
 - [LogPageDownload](docs/LogPageDownload.md)
 - [LsfComputeConfig](docs/LsfComputeConfig.md)
 - [LsfComputeConfigAllOf](docs/LsfComputeConfigAllOf.md)
 - [MemberDbDto](docs/MemberDbDto.md)
 - [MoabComputeConfig](docs/MoabComputeConfig.md)
 - [NavbarConfig](docs/NavbarConfig.md)
 - [NavbarConfigNavbarMenu](docs/NavbarConfigNavbarMenu.md)
 - [OrgAndWorkspaceDto](docs/OrgAndWorkspaceDto.md)
 - [OrgRole](docs/OrgRole.md)
 - [Organization](docs/Organization.md)
 - [OrganizationDbDto](docs/OrganizationDbDto.md)
 - [ParticipantDbDto](docs/ParticipantDbDto.md)
 - [ParticipantType](docs/ParticipantType.md)
 - [PipelineDbDto](docs/PipelineDbDto.md)
 - [PipelineInfo](docs/PipelineInfo.md)
 - [PipelineOptimizationStatus](docs/PipelineOptimizationStatus.md)
 - [PipelineQueryAttribute](docs/PipelineQueryAttribute.md)
 - [PipelineSchemaAttributes](docs/PipelineSchemaAttributes.md)
 - [PipelineSchemaResponse](docs/PipelineSchemaResponse.md)
 - [PipelineSecret](docs/PipelineSecret.md)
 - [PlatformMetainfo](docs/PlatformMetainfo.md)
 - [PodCleanupPolicy](docs/PodCleanupPolicy.md)
 - [ProcessLoad](docs/ProcessLoad.md)
 - [ProgressData](docs/ProgressData.md)
 - [RandomWorkflowNameResponse](docs/RandomWorkflowNameResponse.md)
 - [ResourceData](docs/ResourceData.md)
 - [RunId](docs/RunId.md)
 - [RunListResponse](docs/RunListResponse.md)
 - [RunLog](docs/RunLog.md)
 - [RunRequest](docs/RunRequest.md)
 - [RunStatus](docs/RunStatus.md)
 - [SSHSecurityKeys](docs/SSHSecurityKeys.md)
 - [SecurityKeys](docs/SecurityKeys.md)
 - [ServiceInfo](docs/ServiceInfo.md)
 - [ServiceInfoResponse](docs/ServiceInfoResponse.md)
 - [SlurmComputeConfig](docs/SlurmComputeConfig.md)
 - [State](docs/State.md)
 - [SubmitWorkflowLaunchRequest](docs/SubmitWorkflowLaunchRequest.md)
 - [SubmitWorkflowLaunchResponse](docs/SubmitWorkflowLaunchResponse.md)
 - [Task](docs/Task.md)
 - [TaskStatus](docs/TaskStatus.md)
 - [Team](docs/Team.md)
 - [TeamDbDto](docs/TeamDbDto.md)
 - [TraceBeginRequest](docs/TraceBeginRequest.md)
 - [TraceBeginResponse](docs/TraceBeginResponse.md)
 - [TraceCompleteRequest](docs/TraceCompleteRequest.md)
 - [TraceCompleteResponse](docs/TraceCompleteResponse.md)
 - [TraceCreateRequest](docs/TraceCreateRequest.md)
 - [TraceCreateResponse](docs/TraceCreateResponse.md)
 - [TraceHeartbeatRequest](docs/TraceHeartbeatRequest.md)
 - [TraceHeartbeatResponse](docs/TraceHeartbeatResponse.md)
 - [TraceProcessingStatus](docs/TraceProcessingStatus.md)
 - [TraceProgressData](docs/TraceProgressData.md)
 - [TraceProgressDetail](docs/TraceProgressDetail.md)
 - [TraceProgressRequest](docs/TraceProgressRequest.md)
 - [TraceProgressResponse](docs/TraceProgressResponse.md)
 - [UnivaComputeConfig](docs/UnivaComputeConfig.md)
 - [UpdateActionRequest](docs/UpdateActionRequest.md)
 - [UpdateComputeEnvRequest](docs/UpdateComputeEnvRequest.md)
 - [UpdateCredentialsRequest](docs/UpdateCredentialsRequest.md)
 - [UpdateDatasetRequest](docs/UpdateDatasetRequest.md)
 - [UpdateLabelRequest](docs/UpdateLabelRequest.md)
 - [UpdateLabelResponse](docs/UpdateLabelResponse.md)
 - [UpdateMemberRoleRequest](docs/UpdateMemberRoleRequest.md)
 - [UpdateOrganizationRequest](docs/UpdateOrganizationRequest.md)
 - [UpdateParticipantRoleRequest](docs/UpdateParticipantRoleRequest.md)
 - [UpdatePipelineRequest](docs/UpdatePipelineRequest.md)
 - [UpdatePipelineResponse](docs/UpdatePipelineResponse.md)
 - [UpdatePipelineSecretRequest](docs/UpdatePipelineSecretRequest.md)
 - [UpdateTeamRequest](docs/UpdateTeamRequest.md)
 - [UpdateWorkspaceRequest](docs/UpdateWorkspaceRequest.md)
 - [UploadDatasetVersionResponse](docs/UploadDatasetVersionResponse.md)
 - [UserDbDto](docs/UserDbDto.md)
 - [Visibility](docs/Visibility.md)
 - [WesErrorResponse](docs/WesErrorResponse.md)
 - [WfManifest](docs/WfManifest.md)
 - [WfNextflow](docs/WfNextflow.md)
 - [WfStats](docs/WfStats.md)
 - [Workflow](docs/Workflow.md)
 - [WorkflowDbDto](docs/WorkflowDbDto.md)
 - [WorkflowLaunchRequest](docs/WorkflowLaunchRequest.md)
 - [WorkflowLaunchResponse](docs/WorkflowLaunchResponse.md)
 - [WorkflowLoad](docs/WorkflowLoad.md)
 - [WorkflowLogResponse](docs/WorkflowLogResponse.md)
 - [WorkflowMetrics](docs/WorkflowMetrics.md)
 - [WorkflowQueryAttribute](docs/WorkflowQueryAttribute.md)
 - [WorkflowStatus](docs/WorkflowStatus.md)
 - [Workspace](docs/Workspace.md)
 - [WorkspaceDbDto](docs/WorkspaceDbDto.md)
 - [WspRole](docs/WspRole.md)


## Documentation For Authorization


## BearerAuth

- **Type**: HTTP basic authentication

