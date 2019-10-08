# vue-table
A simple Vue component to display tables. Support sort and pagination options. Configurable css styles for the table

Example with 2 Table components, first one with default styles and paginator and second one with custom css styles and paginator in 'select' mode
[IMG]

## How to configure it
The componet indeed is compound by TableView component (grid) and TablePagination component (paginator)

### TableView component

Props
- `columns`: (required) array with table columns definition (See columns definition)
- `rows`: (required) array with data to fill the table
- `sort`: object with sorting configuration
  - **field**: default sort field
  - **order**: [asc/desc] 
- `pagination`: object with pagination configuration
  - **enabled**: [true/false]
  - **itemsPerPage**: number of rows in each page
  - **align**: [left/center/right] position of the paginator
  - **visualStyle**: [select/button] paginator style
- `cssStyle`: css class that will be applied to the component instead of default styles. Custom styles must be defined in this way:
```
.my-css-style{
    .ozn-table {
        ...
    }
    .ozn-paginator {
        ...
    }
}
```

Columns definition
- **label**: text that will be shown in the column header
- **field**: data field related to the column
- **sortable**: [true/false]
- **type**: [String/Number]

Example


### TablePagination component

Props
- `page`: active page
- `totalPages`: number of pages
- `paginationOptions`: object with pagination configuration. (Same as prop  pagination in TableView component)


## Usage