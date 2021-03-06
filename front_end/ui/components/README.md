# data-grid

The data-grid component takes in tabular data and renders it into a table. It does not provide complex functionality such as sorting or filtering. For that, you should use a `data-grid-controller` component.

## Passing data into the data grid

The data-grid takes in `rows` and `columns` separately. See the type definitions
of these in `DataGridUtils.ts` for an explanation on each individual field.

For example, to construct a table of capital cities around the world, we
might pass in:

```js
const columns = [
  { id: 'city', title: 'City', width: 50 },
  { id: 'country', title: 'Country', width: 50 },
]
# data-grid

The data-grid component takes in tabular data and renders it into a table. It does not provide complex functionality such as sorting or filtering. For that, you should use a `data-grid-controller` component.

## Passing data into the data grid

The data-grid takes in `rows` and `columns` separately. See the type definitions
of these in `DataGridUtils.ts` for an explanation on each individual field.

For example, to construct a table of capital cities around the world, we
might pass in:

```js
const columns = [
  { id: 'city', title: 'City', width: 50 },
  { id: 'country', title: 'Country', width: 50 },
]

const rows = [
  { cells: [
      { columnId: 'city', value: 'London', title: 'London' },
      { columnId: 'country', value: 'UK', title: 'UK' }
    ]
  },
  { cells: [
      { columnId: 'city', value: 'Berlin', title: 'Berlin' },
      { columnId: 'country', value: 'Germany', title: 'Germany' }
    ]
  },
]
```

The field `title` in rows is used as the key for sorting and search as
well for the title attribute of the cell.

# data-grid-controller

A data-grid-controller extends the basic data-grid with more
functionality. It renders a regular data-grid, but contains logic for
filtering and sorting columns.

You create a data-grid-controller in the same way as you create a data-grid, and
the structure of the `rows` and `columns` is identical. Any column you wish to
be sortable should have `sortable: true` set. Currently colums are sorted
alphabetically (or numerically if the values are numbers) in ASC or DESC order.
We do not yet have the ability to provide custom compartor functions for column
sorting.

A data-grid-controller can optionally also take an array of filters. These
should be created via `TextUtils.FilterParser`.

```
const keys = ['city', 'country'];
const parser = new TextUtils.FilterParser(keys);
// Pass this into devtools-data-grid-controller to filter accordingly
const filters = parser.parse('lond')
```
