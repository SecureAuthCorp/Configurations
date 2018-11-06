# Application Templates

Application templates are JSON object files that define an interface and data model for creating an _application_ via the New Web Admin UI.  An application created from one of these templates will translate into one or more _realms_ in the Classic Web Admin UI.


## General Template Configuration

Application templates are rendered using BUTRE (Blueprint Ui Template Rendering Engine) so any of the constructs understood by the renderer can also be used in an application template.

Beyond this, there are template configuration values that are specific to applications.

- `title` string  
A name for the application template.  This should generally depict the type of application this template is capable of creating.  When selecting from a list of application templates in the New UI, this is the value that will display in the __Name__ column.

- `icon` string  
A URL or base64 image icon value.  This value will be used to visually identify the application template in the New UI.

- `templateName` string  
An internal name for the template.  An Application created in the New UI will be associated with this name so that the correct template can be used to edit the application.

- `applicationType` string  
The generic type for this template.  If a template defines an interface for a subset of the configuration fields of another application type then specify that application type here.

- `allowDataUpload` boolean  
Can users upload data into this template?  This defines whether or not an admin user can upload a data file into the template via the New UI.  Generally, this should only be `true` for generic-level templates where data upload files are well defined and understood by the underlying IdP architecture.

- `__devOnly__` boolean  
Hide this template in production?  Setting this to `true` prevents this template from displaying in the New UI.

##  Templates views

Each template consist in 6 views that will be render inside sparkles

- `default` string
This one is the connection settings page of sparkles, is considered the default view of every template, so you will see that is has no `@` identifier.
This page consist on the connection information necessary for each particular application.

- `details`
In here the user can upload a custom image logo, the application name and description if necessary, the Data Stores for the application connection, and Groups.

- `summary`
This page will have the resume of the connection and details view in read only mode. From here you can go to each `update view`.

- `providersInfo`
This page will have the information of Login and Logout URL as well as the issuer and certificate information.

- `updateGroups`
In this page the user can edit the Data Stores and Groups for an already created application.

- `updateDetails`
In this page the user can edit the Application name, description and logo for an already created application.


## Data Sourcing
Templates can pull data from the server using the `source` property on elements that support it.

- `data:dataStores:dataStoreInputList`
Get a list of `Data Stores` availables to be used be the application.

- `options:applianceCertificates:certificateOptions`
Get a list of cerficates availables in the appliance.

- `options:dataStoreProperties:dataStoreOption`
Get a list of profile fields.

## Messages to sparkles
The templates can send specific messages to sparkles with the `clickAction` property, each of them will trigger a specific action in the application.

- **edit groups** `{"actions": "edit groups", "sendToParent": true}` 
Send the message to open the `updateGroups` view of the template

- **see providers** `{"actions": "see providers", "sendToParent": true}` 
Send the message to open the `providersInfo` view

- **edit connection** `{"actions": "edit connection", "sendToParent": true}` 
Send the message to open the `default view` to update connection settings

- **download certificate** `{"actions": "download certificate", "sendToParent": true}` 
Send the message to download the certificate

- **edit details** `{"actions": "edit details", "sendToParent": true}` 
Send the message to open the `updateDetails` view.
