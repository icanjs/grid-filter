# grid-filter
Filter tool for the grid-component

## Intro

Filter is a tool for _grid-component_ designed to filter a list on entered search terms. Its built with CanJS and StealJS
and can be used for CanJS stack including DoneJS (http://donejs.com). Component updated isVisible property of list items
to toggle visibility.

![Filter Demo](./dist/demo.png)Multi Select

## Usage
```html
<grid-filter {(rows)}="rows"></grid-filter>

<grid-filter {(rows)}="rows"
             columns="title,amount"
             {^search-terms}="searchTerms"></grid-filter>
```

### Full grid example
```html
<grid-component {(rows)}="items">

  <div class="grid-tools">

    <grid-filter {(rows)}="rows"></grid-filter>

  </div>

  <table>
    <thead>
      <tr>
        <th ($click)="{sortBy 'title'}">Title {{{sortArrow 'title'}}}</th>
        <th ($click)="{sortBy 'amount'}">Amount {{{sortArrow 'amount'}}}</th>
      </tr>
    </thead>

    <tbody>
      {{#each rows}}
        <tr class="{{^if isVisible}}hidden{{/if}}">
          <td>{{title}}</td>
          <td>{{amount}}</td>
        </tr>
      {{/each}}
    </tbody>
  </table>
</grid-component>
```

## API

- rows: can.List to apply filtering to.
- columns: coma-separated list of columns to filter on. Default is all columns.
- search-terms: a list of search terms entered into filter box.