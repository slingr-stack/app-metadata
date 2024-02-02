# Entity: Contacts

- **Description:** stores contact information
- **Type:** data
- **Full nme:** contacts
- **Version:** 53

## Settings
- **Allow global search:** no
- **Abstract:** no
- **Label calculation type:** script
- **Label calculation script:**
  ```javascript
  return record.field('firstName') + ' ' + record.field('lastName');
  ```
- **Audit Logs:**
  - Enabled: yes
  - User context: 
    - Record created: yes 
    - Record updated: yes 
    - Record deleted: yes 
    - Action executed: yes
  - Script context: 
    - Record created: yes
    - Record updated: yes
    - Record deleted: yes
    - Action executed: yes
  - System context: 
    - Cascade updates: no
    - Refactorings: no
  - Detailed logging: no
- **Indexes:**
  - Name: email
    - Type: regular
    - Unique: yes
    - Fields:
      - Name: email
        - Label: Email

## Fields
1. **First name**
  - Type: text
  - Multiplicity: one
  - Description: The first name of the contact
  - Rules:
    - Default value: none
    - Required: always
    - Unique: no
    - Indexable: no
    - Transient: no
    - Sensitive: no
    - Calculated: no
    - Read access: always
    - Write access: always
  - Type rules:
    - Max length: empty
    - Min length: empty
    - Exact length: empty
    - Regular expression: empty
    - Regular expression hint: empty
  - Display options:
    - Element type: entity field view
    - Read only: never
    - Visible: always
    - Show label: yes
    - Value alignment: left
    - Representation: input box
    - Limit number of characters: no

2. **Last Name**
  - Type: text
  - Multiplicity: one
  - Description: The last name of the contact
  - Rules:
    - Default value: none
    - Required: always
    - Unique: no
    - Indexable: no
    - Transient: no
    - Sensitive: no
    - Calculated: no
    - Read access: always
    - Write access: always
  - Type rules:
    - Max length: empty
    - Min length: empty
    - Exact length: empty
    - Regular expression: empty
    - Regular expression hint: empty
  - Display options:
    - Element type: entity field view
    - Read only: never
    - Visible: always
    - Show label: yes
    - Value alignment: left
    - Representation: input box
    - Limit number of characters: no

3. **Company**
  - Type: relationship
  - Multiplicity: one
  - Description: The company that the contact belongs to
  - Rules:
    - Default value: none
    - Required: always
    - Unique: no
    - Indexable: no
    - Transient: no
    - Sensitive: no
    - Calculated: no
    - Read access: always
    - Write access: always
  - Type rules:
    - Target entity: companies
    - Filter:
      - Condition: and
      - Rules:
        - Field: active
          - Operator: equals
          - Value: yes
    - Cascade operations:
      - Delete policy: remove relationship
      - Update label: yes
      - Update available fields: yes
  - Display options:
    - Element type: entity field view
    - Read only: never
    - Visible: always
    - Show label: yes
    - Value alignment: left
    - Representation: drop down
    - Read only representation: plain text
    - Sort Field: id
    - Sort Type: desc
    - Enable link: no
    - Allow to create new record: no
    - Allow to edit record: no
    - Visible fields:
      - Name: active
        - Use default display options: yes
      - Name: services
        - Use default display options: yes

## Actions
1. **Log full name**
  - Type: oneRecord
  - Description: Logs the full name of the contact
  - Settings:
    - Precondition: none
    - Visible: always
    - Async: no
    - Save linked parameters: no
    - Result as response: no
  - Operation type: script
  - Operation script: 
  ```javascript
  sys.logs.info('The full name is: ' + record.field('firstName').val() + ' ' + record.field('lastName').val());
  ```
