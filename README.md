# Role Name

Helper role to configure AAP Controller using modules.

## Requirements

The role requires the **ansible.controller** collection.

## Role Variables

### Configure SCM Credentials

| Name                | Description                                               | Mandatory | Defaults |
| ------------------- | --------------------------------------------------------- | --------- | -------- |
| controller_host     | The hostname or IP address of the controller.             | ✔️        |          |
| controller_username | The username for authentication to the controller.        | ✔️        |          |
| controller_password | The password for authentication to the controller.        | ✔️        |          |
| organization        | The organization in the controller. Default is "Default". | ✔️        |          |
| validate_certs      | Whether to validate SSL certificates. Default is `false`. | ✔️        |          |

#### Structure for aap2_scm_credentials

| Name         | Description                              | Mandatory | Defaults |
| ------------ | ---------------------------------------- | --------- | -------- |
| name         | The name of the SCM credential.          | ❌        |          |
| scm_username | The username for SCM authentication.     | ❌        |          |
| scm_password | The password for SCM authentication.     | ❌        |          |
| scm_ssh_key  | The SSH key data for SCM authentication. | ❌        |          |

### Configure Machine Credentials

| Name                | Description                                        | Mandatory | Defaults |
| ------------------- | -------------------------------------------------- | --------- | -------- |
| controller_host     | The hostname or IP address of the controller.      | ✔️        |          |
| controller_username | The username for authentication to the controller. | ✔️        |          |
| controller_password | The password for authentication to the controller. | ✔️        |          |
| organization        | The organization in the controller.                | ✔️        | Default  |
| validate_certs      | Whether to validate SSL certificates.              | ❌        | false    |

#### Structure for aap2_machine_credentials

| Name     | Description                              | Mandatory | Defaults |
| -------- | ---------------------------------------- | --------- | -------- |
| name     | The name of the machine credential.      | ✔️        |          |
| username | The username for machine authentication. | ✔️        | sysadmin |
| password | The password for machine authentication. | ✔️        | redhat   |

### Configure Cloud Credentials

| Name                | Description                                        | Mandatory | Defaults |
| ------------------- | -------------------------------------------------- | --------- | -------- |
| controller_host     | The hostname or IP address of the controller.      | ✔️        |          |
| controller_username | The username for authentication to the controller. | ✔️        |          |
| controller_password | The password for authentication to the controller. | ✔️        |          |
| organization        | The organization in the controller.                | ✔️        | Default  |
| validate_certs      | Whether to validate SSL certificates.              | ❌        | false    |

#### Structure for aap2_cloud_credentials

| Name            | Description                                   | Mandatory | Defaults |
| --------------- | --------------------------------------------- | --------- | -------- |
| name            | The name of the cloud credential.             | ✔️        |          |
| credential_type | The type of cloud credential.                 | ✔️        |          |
| tenant          | The Azure tenant ID.                          | ❌        |          |
| subscription    | The Azure subscription ID.                    | ❌        |          |
| client          | The Azure client ID.                          | ❌        |          |
| secret          | The Azure secret key.                         | ❌        |          |
| username        | The AWS access key ID for authentication.     | ❌        |          |
| password        | The AWS secret access key for authentication. | ❌        |          |

### Configure Projects

| Name                | Description                                        | Mandatory | Defaults |
| ------------------- | -------------------------------------------------- | --------- | -------- |
| controller_host     | The hostname or IP address of the controller.      | ✔️        |          |
| controller_username | The username for authentication to the controller. | ✔️        |          |
| controller_password | The password for authentication to the controller. | ✔️        |          |
| organization        | The organization in the controller.                | ✔️        | Default  |
| validate_certs      | Whether to validate SSL certificates.              | ❌        | false    |

#### Structure for aap2_projects

| Name                 | Description                                        | Mandatory | Defaults                        |
| -------------------- | -------------------------------------------------- | --------- | ------------------------------- |
| name                 | The name of the project.                           | ✔️        | "AAP2 Controller Setup"         |
| scm_update_on_launch | Whether to update the project on launch.           | ❌        | true                            |
| scm_type             | The type of source control system.                 | ❌        | git                             |
| scm_branch           | The branch to use in the source control system.    | ❌        | main                            |
| scm_url              | The URL to the source control repository.          | ✔️        |                                 |
| scm_credential       | The SCM credential to use for authentication.      | ❌        |                                 |
| update_project       | Whether to force an update to the project.         | ❌        | true                            |
| default_environment  | The default execution environment for the project. | ❌        | "Default execution environment" |

#### Configure Inventory

| Name                | Description                                        | Mandatory | Defaults |
| ------------------- | -------------------------------------------------- | --------- | -------- |
| controller_host     | The hostname or IP address of the controller.      | ✔️        |          |
| controller_username | The username for authentication to the controller. | ✔️        |          |
| controller_password | The password for authentication to the controller. | ✔️        |          |
| organization        | The organization in the controller.                | ✔️        | Default  |
| validate_certs      | Whether to validate SSL certificates.              | ❌        | false    |

##### Structure for aap2_inventories

| Name                | Description                | Mandatory | Defaults |
| ------------------- | -------------------------- | --------- | -------- |
| aap2_inventory_name | The name of the inventory. | ✔️        |          |

#### Configure Inventory Sources

| Name                | Description                                        | Mandatory | Defaults |
| ------------------- | -------------------------------------------------- | --------- | -------- |
| controller_host     | The hostname or IP address of the controller.      | ✔️        |          |
| controller_username | The username for authentication to the controller. | ✔️        |          |
| controller_password | The password for authentication to the controller. | ✔️        |          |
| organization        | The organization in the controller.                | ✔️        | Default  |
| validate_certs      | Whether to validate SSL certificates.              | ❌        | false    |

##### Structure for aap2_inventory_sources

| Name                            | Description                                             | Mandatory | Defaults |
| ------------------------------- | ------------------------------------------------------- | --------- | -------- |
| aap2_inventory_source_name      | The name of the inventory source.                       | ✔️        |          |
| aap2_inventory_source_inventory | The inventory in which the source should be created.    | ✔️        |          |
| aap2_inventory_source_type      | The type of inventory source.                           | ✔️        |          |
| overwrite                       | Whether to overwrite the inventory source.              | ❌        | true     |
| overwrite_vars                  | Whether to overwrite variables in the inventory source. | ❌        | true     |
| update_on_launch                | Whether to update the inventory source on launch.       | ❌        | true     |
| credential                      | The credential to use for authentication.               | ❌        |          |
| source_path                     | The path to the inventory source.                       | ❌        |          |
| source_project                  | The project containing the inventory source.            | ❌        |          |
| source_vars                     | The variables to use for the inventory source.          | ❌        |          |

#### Configure Templates

| Name                | Description                                        | Mandatory | Defaults |
| ------------------- | -------------------------------------------------- | --------- | -------- |
| controller_host     | The hostname or IP address of the controller.      | ✔️        |          |
| controller_username | The username for authentication to the controller. | ✔️        |          |
| controller_password | The password for authentication to the controller. | ✔️        |          |
| organization        | The organization in the controller.                | ✔️        | Default  |
| validate_certs      | Whether to validate SSL certificates.              | ❌        | false    |

##### Structure for aap2_templates

| Name                         | Description                                     | Mandatory | Defaults              |
| ---------------------------- | ----------------------------------------------- | --------- | --------------------- |
| aap2_template_name           | The name of the template.                       | ✔️        |                       |
| aap2_template_inventory      | The inventory associated with the template.     | ✔️        |                       |
| aap2_template_project        | The project associated with the template.       | ❌        | AAP2 Controller Setup |
| aap2_template_playbook       | The playbook to be executed by the template.    | ✔️        |                       |
| aap2_template_survey_enabled | Whether the survey is enabled for the template. | ❌        | false                 |
| aap2_template_survey_spec    | The specification for the survey.               | ❌        |                       |
| aap2_template_credentials    | The credentials to be used by the template.     | ❌        |                       |
| aap2_template_ask_vars       | Whether to prompt for variables during launch.  | ❌        | false                 |

#### Configure Workflows

| Name                | Description                                        | Mandatory | Defaults |
| ------------------- | -------------------------------------------------- | --------- | -------- |
| controller_host     | The hostname or IP address of the controller.      | ✔️        |          |
| controller_username | The username for authentication to the controller. | ✔️        |          |
| controller_password | The password for authentication to the controller. | ✔️        |          |
| organization        | The organization in the controller.                | ✔️        | Default  |
| validate_certs      | Whether to validate SSL certificates.              | ❌        | false    |

##### Structure for aap2_workflows

| Name                         | Description                                     | Mandatory | Defaults |
| ---------------------------- | ----------------------------------------------- | --------- | -------- |
| aap2_workflow_name           | The name of the workflow.                       | ✔️        |          |
| aap2_workflow_survey_enabled | Whether the survey is enabled for the template. | ❌        | false    |
| aap2_workflow_survey_spec    | The specification for the survey.               | ❌        |          |
| aap2_workflow_nodes          | Spec of workflow nodes                          | ✔️        |          |

##### Structure for aap2_workflow_nodes

| Name              | Description                    | Mandatory | Defaults |
| ----------------- | ------------------------------ | --------- | -------- |
| node_name         | The name of the workflow.      | ✔️        |          |
| node_job_template | The job template of the node.  | ✔️        |          |
| nodes_on_success  | The node(s) to link on success | ❌        | omit     |
| nodes_on_fail     | The node(s) to link on fail    | ❌        | false    |

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - name: Configure AAP2 Controller Resources
      hosts: localhost
      gather_facts: false

      vars:
        aap2_controller_url: "your_controller_host"
        aap2_controller_username: "your_controller_username"
        aap2_controller_password: "your_controller_password"
        aap2_organization: "your_organization"

        aap2_machine_credentials:
          - name: "My Machine Credential"
            username: "my_machine_username"
            password: "my_machine_password"

        aap2_projects:
          - name: "My Project"
            scm_type: "git"
            scm_url: "https://github.com/your_username/your_project.git"

        aap2_inventories:
          - aap2_inventory_name: "My Inventory"

        aap2_inventory_sources:
          - aap2_inventory_source_name: "My Inventory Source"
            aap2_inventory_source_inventory: "My Inventory"
            aap2_inventory_source_type: "My Inventory Source Type"
            # Add other required inputs here

        aap2_templates:
          - aap2_template_name: "My Template"
            aap2_template_inventory: "My Inventory"
            aap2_template_project: "My Project"
            aap2_template_playbook: "path/to/your/playbook.yml"
          - aap2_template_name: "My Template 2"
            aap2_template_inventory: "My Inventory"
            aap2_template_project: "My Project"
            aap2_template_playbook: "path/to/your/playbook.yml"

        aap2_workflows:
          - aap2_workflow_name: "My Workflow"
            aap2_workflow_nodes:
              - node_name: node1
                nodes_on_success:
                  - node2
                node_job_template: "My Template"
              - name: node2
                node_job_template: "My Template 2"

      roles:
        - role: role_aap_controller_setup

## License

BSD

## Author Information

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
