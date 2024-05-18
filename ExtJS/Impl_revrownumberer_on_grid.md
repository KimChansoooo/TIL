# Implement Reverse Rownumberer

> ExtJS에는 그리드의 열번호를 표현해주는 rownumberer 컴포넌트가 존재한다.
> 
> rownumberer은 정순을 표현해주기 때문에, 역순 채번이 필요했고 기존 컴포넌트를 확장하여 역순으로 채번되게 사용할 수 있다.

*****

##### RowNumberer
```javascript
columns: [
    {xtype: 'rownumberer'}      // Ext.grid.column.RowNumberer 컴포넌트
]
```

<br/>

##### RevRowNumberer

```javascript
columns: [
    {xtype: 'revrownumberer'}      // 재정의한 컴포넌트
]
```

```javascript
/**
 * Description     : 역순 RowNumberer
 */
Ext.define('Ext.view.widget.panel.RevRowNumberer', {
    extend: 'Ext.grid.column.RowNumberer',
    alias: 'widget.revrownumberer',

    defaultRenderer: function(value, metaData, record, rowIdx, colIdx, dataSource, view) {
        /**
         * viewModel totalProperty 값을 참조하기 때문에
         * row 추가 시 store.totalCount를 늘려주고, 삭제 시 줄여줘야 정상 동작됨
         */
        var totalCount = dataSource.getTotalCount();
        var currentPage = dataSource.currentPage;
        var result;

        if (record) {
            result = totalCount - dataSource.indexOf(record);
        } else {
            result = totalCount - value;
        }

        if (currentPage && currentPage > 1) {
            result -= (currentPage - 1) * dataSource.pageSize;
        }

        return result;
    },

    updater: function(cell, value, record, view, dataSource) {
        var cellInner = cell && cell.querySelector(view.innerSelector);

        if (cellInner) {
            cellInner.innerHTML = this.defaultRenderer(value - 1, null, record, null, null, dataSource, view);
        }
    }
});
```


