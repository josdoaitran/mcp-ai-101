# Ideas
- Take advantages of LLM to help us generate test case with a specify template via prompting
- Integrate MCP to push the generated Test Cases into Excel file, where we use it to manage test cases for a specify project.

# Tools and Setup MCP Server
- Using Cursor, VSCode with Copilot, Claude
- Configure MCP for Execel: https://github.com/negokaz/excel-mcp-server
MCP Excel server is automatically installed by adding the following configuration to the MCP servers configuration
https://github.com/negokaz/excel-mcp-server

## Windows
```json
{
    "mcpServers": {
        "excel": {
            "command": "cmd",
            "args": ["/c", "npx", "--yes", "@negokaz/excel-mcp-server"],
            "env": {
                "EXCEL_MCP_PAGING_CELLS_LIMIT": "4000"
            }
        }
    }
}
```

## MAC / Linux
```json
{
    "mcpServers": {
        "excel": {
            "command": "npx",
            "args": ["--yes", "@negokaz/excel-mcp-server"],
            "env": {
                "EXCEL_MCP_PAGING_CELLS_LIMIT": "4000"
            }
        }
    }
}
```

![walking](https://josdoaitran.github.io/assets/images/ai-for-testing/mcp-test-cases/claude-desktop-mcp-excel.png)


# Example Prompting to controll MCP Server for testing purpose

```
You can check this Excel file {{path_your_excel_file}}
How many sheets in this file ?
```
![walking](https://josdoaitran.github.io/assets/images/ai-for-testing/mcp-test-cases/mcp-excel-read-file.png)

![walking](https://josdoaitran.github.io/assets/images/ai-for-testing/mcp-test-cases/mcp-excel-count-sheet.png)

```
As a QA engineer and to prepare an Excel file to cover testing for a mobile app.

Please help me generate the excel template for manage test cases purpose into sheet: Sheet1 in this file: {{path_your_excel_file}} ?
```

Generated test cases in Excel
![walking](https://josdoaitran.github.io/assets/images/ai-for-testing/mcp-test-cases/generated-testcase-excel.png)

```
Please refactoring all template for my test cases management in excel sheet `Sheet1`.
how it is compatible with BDD Given When Then format.
```

![walking](https://josdoaitran.github.io/assets/images/ai-for-testing/mcp-test-cases/mcp-excel-refactor-to-bdd.png)

Besides, Claude AI gave me the BDD test cases template where we can refer, review and request to update more in case AI template is not enough good as we expect.
![walking](https://josdoaitran.github.io/assets/images/ai-for-testing/mcp-test-cases/ai-claude-mcp-bdd-testcase-template.png)