# How to Contribute to an OSF Add-on (GraveyValet)

## Introduction

The Open Science Framework (OSF) supports a range of third-party services through add-ons, allowing researchers to seamlessly integrate external tools such as cloud storage, data repositories, and other platforms into their workflows. By leveraging these integrations, researchers can improve data accessibility, maintain version control, and streamline collaboration within their projects.

The OSF Addon Service, also known as GraveyValet, is a Python-based microservice for managing access to and interactions between the OSF and external services. Beyond serving as a central source for handling these interactions, the OSF Addon Service provides a set of tools for writing new integrations in a consistent manner.

GravyValet's code documentation can be found [here](https://addons.staging.osf.io/static/gravyvalet_code_docs/index.html#gravyvalet).

## Understanding OSF Add-ons

An OSF add-on is an extension that facilitates the interaction between OSF and external services. Each add-on must adhere to OSF’s integration framework to ensure compatibility and security.

### Key Components

- **Interface System**: Defines the protocols for communication between OSF and add-ons.
- **Implementation Module (Imp)**: Contains the logic required to interact with the third-party service.
- **Authentication**: Uses secure protocols (e.g., OAuth 2.0) to establish trusted connections.
- **User Interface**: Provides OSF users with configuration and access options within the platform.

## Supported Add-ons

OSF currently supports various add-ons for cloud storage (e.g., Google Drive, Dropbox), repositories (e.g., GitHub), and data archiving (e.g., Dataverse). Researchers can enable or disable these integrations through their OSF settings.

## Contribution Process

### 1. Identify the Need

Before developing a new add-on, evaluate its necessity by:

- Assessing gaps in existing OSF functionality.
- Gathering feedback from the OSF community.
- Identifying widely-used research tools that could benefit from OSF integration.

### 2. Review Existing Implementations

To ensure consistency, study OSF’s current add-ons:

- Analyze authentication workflows and data retrieval methods.
- Examine code structures and API interaction patterns.
- Review community discussions and feature requests related to add-ons.

### 3. Set Up Development Environment

To begin development:

- Clone the OSF repository from GitHub.
- Install required dependencies and libraries.
- Set up a local testing environment to validate add-on functionality.

### 4. Develop the Add-on

- **Define Authentication**: Implement secure login mechanisms to authorize users.
- **Integrate with API**: Ensure smooth data exchange between OSF and the external service.
- **Create a User-Friendly UI**: Provide intuitive controls for enabling and managing the add-on.
- **Implement Logging and Error Handling**: Ensure issues are logged for debugging and user support.

### 5. Submit for Review

Before submitting your add-on:

- Ensure adherence to OSF’s coding and security standards.
- Provide detailed documentation, including setup instructions and use cases.
- Submit a pull request for review, incorporating feedback from OSF maintainers.

## Technical Guide to Contributing OSF Add-ons

### Implementing an OSF Add-on

#### Identify the Addon Interface(s)

The first step to contributing a new OSF Addon is to determine which supported interfaces your service implements. Each Interface defines a set of supported Operations that a remote service implementing the interface might support. Each Operation will be decorated with either:

`@immediate_operation`: Directly returns the normalized result of an external API behavior – i.e. the list of items in a directory for a Storage Implementation.

`@redirect_operation`: Returns a link to the remote service that the caller can use to perform the desired behavior (i.e. downloading a remote file)

`@eventual_operation`: Initiates a long-running operation asynchronously with a promise of surfacing the result once it is complete (i.e. uploading a remote file).

Beyond providing arguments to the decorator to describe the required permission-level for the operation, the function signature doubles as the normalized payload/response definition for the Operation in the API. Return types, in particular, are defined in terms of Data Classes that are used to generate JSONSchemas and perform validation. e.g.

```python
    @immediate_operation(capability=AddonCapabilities.ACCESS)
    async def list_child_items(
        self,
        item_id: str,
        page_cursor: str = "",
        item_type: ItemType | None = None,
    ) -> ItemSampleResult: ...
```

It’s possible that your service supports multiple interfaces. Archival Repositories, for example, could be understood as providing a Storage Interface (for accessing the archived data) and an Archival Interface (if the service allows for us to submit data to it). If so, you will need to write a separate integration for each interface.

The full list of currently supported Interfaces can be found in the [addon_toolkit/interfaces directory](https://github.com/CenterForOpenScience/gravyvalet/tree/develop/addon_toolkit/interfaces) of our GitHub repository. If you are not sure about your potential integration or are looking for help defining a new interface, please let us know.

### Writing an Imp (Implementation Module)

The Implementation Module (Imp) serves as the core of the add-on, defining its interaction with external services.

#### Examine Existing Imps
If an interface definition has been released, then you may be able to reference an existing Imp. These can be found in the [addon_imps directory](https://github.com/CenterForOpenScience/gravyvalet/tree/develop/addon_imps) of our GitHub repository under the subdirectory for your interface.

#### Idenfity Supported Operations and Writing the Imp
Determine which operations your service supports. Each interface defines a set of operations that _can_ be supported by a remote service, but not every service needs to support every operation. Figure out what subset of operations you want to define. Then you can subclass the BaseImp class for your interface and implement the subset of operations you want to support.

#### Key Considerations

- **API Integration**: Ensure compatibility with RESTful APIs or other service protocols.
- **Security**: Utilize encrypted connections and follow best practices for data protection.
- **Performance Optimization**: Minimize API calls and implement caching strategies to reduce load times.

### Testing Your Add-on

To ensure robust functionality:

- Conduct unit and integration tests covering key scenarios.
- Validate authentication and authorization mechanisms.
- Test error handling and recovery processes.

#### Register the Imp and Service
To test your implementation, you will need to register the Imp by adding it to our [static mapping](https://github.com/CenterForOpenScience/gravyvalet/blob/develop/addon_service/common/known_imps.py). `_KnownAddonImps` is used to register a name for your Imp, while `_AddonImpNumbers` registers a mapping from that name to an arbitrary-but-unique Database ID.

Finally, you’ll need to register your Service by providing the information to complete an External[Interface]Service entry. This will include generic information – like name,  API root, auth format – as well as interface-specific information – like the maximum number of concurrent uploads a storage service supports. It will also require that integer ID you added to `_AddonImpNumbers`.

<!-- TODO: will likely need some additional documentation on how to test the impelementation either using GV API or using the Frontend -->

## Best Practices for OSF Add-ons

- Follow OSF’s coding and security guidelines.
- Maintain comprehensive documentation for users and developers.
- Engage with the OSF community for feedback and continuous improvement.
- Provide real-world case examples demonstrating successful integrations.

---

By adhering to these principles, contributors can develop reliable and impactful add-ons, enhancing OSF’s capabilities and supporting open science initiatives.
