<template>
    <ag-grid-vue style="width: 2000px; height: 1500px" class="ag-theme-alpine" :columnDefs="columnDefs" :rowData="rowData"
        rowSelection="multiple" :autoGroupColumnDef="autoGroupColumnDef" :defaultColDef="defaultColDef" >
    </ag-grid-vue>
</template>
  
<script lang="ts">
import Vue from 'vue'
import 'ag-grid-enterprise';
import { AgGridVue } from 'ag-grid-vue';

import "ag-grid-community/styles/ag-grid.css";
import "ag-grid-community/styles/ag-theme-alpine.css";

export default {
    name: "App",
    data(): {
        columnDefs: any[] | null;
        rowData: any[] | null;
        autoGroupColumnDef: {
            headerName: string;
            field: string;
            cellRenderer: string;
            cellRendererParams: {
                checkbox: boolean;
            }
        };
        defaultColDef: {
            resizable: boolean;
        };
    } {
        return {
            columnDefs: null,
            rowData: null,
            autoGroupColumnDef: {
                headerName: "ИНН",
                field: "INN",
                cellRenderer: "agGroupCellRenderer",
                cellRendererParams: {
                    checkbox: true,
                },
            },
            defaultColDef: {
                resizable: true,
            },
        };      
    },
    components: {
        AgGridVue,
    },
    beforeMount() {
        this.columnDefs = [
            { field: 'DATESTAMP', headerName: 'Дата и время' },
            { field: 'INSTRUMENT_ID' },
            { field: 'LIST_SECTION', rowGroup: true, hide: true, },
            { field: 'RN' },
            { field: 'SUPERTYPE', headerName: 'Супертип' },
            { field: 'INSTRUMENT_TYPE' },
            { field: 'INSTRUMENT_CATEGORY' },
            { field: 'TRADE_CODE' },
            { field: 'ISIN', filter: true},
            { field: 'REGISTRY_NUMBER' },
            { field: 'REGISTRY_DATE' },
            { field: 'EMITENT_FULL_NAME', filter: true },
            { field: 'INN', headerName: 'ИНН', rowGroup: true, hide: true, filter: true },
            { field: 'NOMINAL' },
            { field: 'CURRENCY' },
            { field: 'ISSUE_AMOUNT' },
            { field: 'DECISION_DATE' },
            { field: 'OKSM_EDR' },
            { field: 'ONLY_EMITENT_FULL_NAME' },
            { field: 'REG_COUNTRY' },
            { field: 'QUALIFIED_INVESTOR' },
            { field: 'HAS_PROSPECTUS' },
            { field: 'IS_CONCESSION_AGREEMENT' },
            { field: 'IS_MORTGAGE_AGENT' },
            { field: 'INCLUDED_DURING_CREATION' },
            { field: 'SECURITY_HAS_DEFAULT' },
            { field: 'SECURITY_HAS_TECH_DEFAULT' },
            { field: 'INCLUDED_WITHOUT_COMPLIANCE' },
            { field: 'RETAINED_WITHOUT_COMPLIANCE' },
            { field: 'HAS_RESTRICTION_CIRCULATION' },
            { field: 'LISTING_LEVEL_HIST' },
            { field: 'OBLIGATION_PROGRAM_RN' },
            { field: 'COUPON_PERCENT' },
            { field: 'EARLY_REPAYMENT' },
            { field: 'EARLY_REDEMPTION' },
            { field: 'ISS_BOARDS' },
            { field: 'OTHER_SECURITIES' },
            { field: 'DISCLOSURE_PART_PAGE' },
            { field: 'DISCLOSURE_RF_INFO_PAGE' },
            { field: 'INCLUDE_DATE' },
            { field: 'CFI_FOREIGN' },
            { field: 'ISIN_UNDERLYING_ASSET' },
            { field: 'CFI_UNDERLYING_ASSET' },
            { field: 'PIF_STATUS' },
            { field: 'PIF_STATUS_HIST' },
            { field: 'OBLIGATION_PROGRAM_DATE' },
            { field: 'ISS_BOARDS_HASH' },
            { field: 'OTHER_SECURITIES_HASH' },
            { field: 'CACHING_TIMESTAMP' },

        ];

        fetch("https://script.googleusercontent.com/macros/echo?user_content_key=u-hbsPCpakD7hvexZ4D24rmo1Em1FtdYzSTg3eQCgIBec-IBXUthNKWsHRrVrGMva1yiUWy5K1voqcYr815-N1OsXYMnGvq2m5_BxDlH2jW0nuo2oDemN9CCS2h10ox_1xSncGQajx_ryfhECjZEnLH5dwAY7lBNz5GCzTnHsCT2OmQV4QsKEYYXB8V8nSIF4dqeez77u-JB-JyYp0bnLk2WmnABeaatFZaPKEIZ0qD86K-cvOlk3dz9Jw9Md8uu&lib=MH9l2wY_JYDrok9VruR-xZhyZ61ymoi4_")
            .then((response) => response.json())
            .then((rowData) => this.rowData = rowData.data)
    },
};
</script>
  