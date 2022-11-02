<template>
  <ejs-treegrid :dataSource="data" childMapping="Children" :allowPaging="true"
    :treeColumnIndex="0" :height='450' :rowHeight="83" :rowTemplate="'customTemplate'">
    <e-columns>
      <e-column field='EmpID' headerText='Employee ID' width='180'></e-column>
      <e-column field='Name' headerText='Employee Name'></e-column>
      <e-column headerText='Employee Details' width='350'></e-column>
      <e-column field='DOB' headerText='DOB'></e-column>
    </e-columns>
    <template v-slot:customTemplate="{data}">
      <tr>
        <td class="border" style="padding-left: 18px;">
          <span>{{data.EmpID}}</span>
        </td>
        <td class="border" style="padding: 10px 0 0 20px;">
          <div style="font-size: 14px;">
            {{data.Name}}
            <p style="font-size: 9px;">{{data.Designation}}</p>
          </div>
        </td>
        <td class="border">
          <div>
            <div style="position: relative;display:inline-block">
              <img :src="'https://ej2.syncfusion.com/vue/demos/source/tree-grid/images/'+ data.FullName + '.png'"
                alt="data.FullName"/>
            </div>
            <div style="display: inline-block;">
              <div style="padding: 5px;">{{data.Address}}</div>
              <div style="padding: 5px;">{{data.Country}}</div>
              <div style="padding: 5px;font-size: 12px;">{{data.Contact}}</div>
            </div>
          </div>
        </td>
        <td class="border" style="padding-left: 20px;">
          <span>{{format(data.DOB)}}</span>
        </td>
      </tr>
    </template>
  </ejs-treegrid>
</template>
<script>
import { TreeGridComponent, ColumnsDirective, ColumnDirective, Page } from "@syncfusion/ej2-vue-treegrid";
import {employeeData} from './data.js';
import {Internationalization} from '@syncfusion/ej2-base';
let object = new Internationalization();
export default{
  name: 'App',
  components: {
    'ejs-treegrid': TreeGridComponent,
    'e-columns': ColumnsDirective,
    'e-column': ColumnDirective
  },
  data: () => {
    return {
      data: employeeData
    }
  },
  methods:{
    format(date){
      return object.formatDate(date,{skeleton:'yMd', type:'date'})
    }
  },
  provide:{
    treegrid: [Page]
  }
}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-treegrid/styles/material.css";

  #app{
    max-width: 80%;
  }

  .border{
    border: solid #e0e0e0;
    border-width: 1px 0 0 0;
  }
</style>
