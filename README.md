# Release Information

- **Version**: 1.0.1

- **Certified**: Yes

- **Publisher**: Fortinet

- **Scope**: Data Access and Retrieval, Insights

- **Verified with Models**: Fortinet FortiAI (AI model Medium)

- [Release notes](./fortisoar-data-access/release_notes.md)

# FortiSOAR Data Access

A read-only FortiSOAR query agent that interprets natural-language security queries, identifies the relevant module, applies filters, and fetches matching records along with correlated data from related modules. It returns the requested records and never creates, updates, or deletes records. It queries one primary module and its correlated module at a time.

## Installation

This agent installs along with the FortiAI solution pack.

## Configuration

The FortiSOAR Data Access agent ships with a configuration that has access to all shipped MCP servers. For custom configuration, refer to the *Configuration* section of the [FortiAI](https://github.com/fortinet-fortisoar/solution-pack-fortinet-advisor) solution pack documentation.

> [!Note]
> Refer to [Configuring MCP Servers](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/823139/mcp-servers#Configure_MCP_Servers) on FortiSOAR platform documentation for information on configuring a custom MCP server.

### Prerequisites

- The FortiAI solution pack must be installed and configured with the Fortinet FortiAI connector.

  - To configure the FortiAI solution pack, refer to the [FortiAI](https://github.com/fortinet-fortisoar/solution-pack-fortinet-advisor/) solution pack documentation.
  - To configure the Fortinet FortiAI connector, refer to the [Fortinet FortiAI](https://docs.fortinet.com/fortisoar/connectors/fortinet-fortiai) connector documentation.

> [!Note]
>
> FortiAI solution pack and Fortinet FortiAI connector are preconfigured out-of-the-box with FortiSOAR `v8.0.0` and later.
> 


## Input Parameters

The input must be provided as a JSON object.

| Parameter               | Description                                                                                         |
|-------------------------|-----------------------------------------------------------------------------------------------------|
| `natural_language_task` | Description of what data should be retrieved from FortiSOAR, including any filters or conditions.   |
|`data`|Output from a previous agent in this conversation, if any. May be empty, a single record, a list of records, or any other JSON shape. When the natural-language task references this data ('the alerts from above', 'those assets'), record ids/uuids from it are used to build the filter; otherwise it is ignored.|
| `user_context`          | Logged-in user context.                                                                             |

## Response

The output is returned as a JSON object.

| Parameter  | Description                                                                            |
|------------|----------------------------------------------------------------------------------------|
| `status`   | Indicates whether the request completed successfully or failed.                        |
| `metadata` | Additional details about the query execution, such as execution mode and record count. |
| `data`     | List of records returned from the FortiSOAR based on the request.                      |
| `url`      | Query string or reference used to fetch the records for traceability.                  |
