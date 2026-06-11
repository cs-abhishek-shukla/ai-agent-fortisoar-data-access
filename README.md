# Release Information

- **Version**: 1.0.0

- **Certified**: Yes

- **Publisher**: Fortinet

- **Scope**: Data Access and Retrieval, Insights

- **Verified with Models**: Fortinet FortiAI (AI model Medium)

# FortiSOAR Data Access

A SOAR agent that accepts natural-language security queries, automatically determines the relevant FortiSOAR module, retrieves matching records with intelligent filtering, extracts key information, and combines data from related modules (Indicators, Reputation, Assets, SLA, MITRE) to deliver a comprehensive, unified response.

## Installation

This agent installs along with the FortiAI solution pack.

## Configuration

**Default MCP Server**: Utility Tools, FortiSOAR Module Management

> [!Note]
>
> Refer to [Configuring MCP Servers](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/823139/mcp-servers#Configure_MCP_Servers) on FortiSOAR platform documentation for information on configuring a custom MCP server.
> 

### Prerequisites

- The FortiAI solution pack must be installed and configured with the Fortinet FortiAI connector.

  - To configure the FortiAI solution pack, refer to the [FortiAI](https://github.com/fortinet-fortisoar/solution-pack-fortinet-advisor/) solution pack documentation.
  - To configure the Fortinet FortiAI connector, refer to the [Fortinet FortiAI](https://docs.fortinet.com/fortisoar/connectors/fortinet-fortiai) connector documentation.

> [!Note]
>
> FortiAI solution pack and Fortinet FortiAI connector are preconfigured out-of-the-box with FortiSOAR `v8.0.0`.
> 


## Input Parameters

The input must be provided as a JSON object.

| Parameter               | Description                                                                                         |
|-------------------------|-----------------------------------------------------------------------------------------------------|
| `natural_language_task` | Description of what data should be retrieved from FortiSOAR, including any filters or conditions.   |
| `objective`             | The purpose of the request and what the retrieved data is expected to help accomplish.              |
| `chain_of_thought`      | Logical reasoning that guides how the objective should be interpreted to retrieve the correct data. |
| `entities`              | Fields to be parse after fetching record.                                                           |
| `user_context`          | Logged-in user context.                                                                             |

## Response

The output is returned as a JSON object.

| Parameter  | Description                                                                            |
|------------|----------------------------------------------------------------------------------------|
| `status`   | Indicates whether the request completed successfully or failed.                        |
| `metadata` | Additional details about the query execution, such as execution mode and record count. |
| `data`     | List of records returned from the FortiSOAR based on the request.                      |
| `url`      | Query string or reference used to fetch the records for traceability.                  |

