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


