<script lang="ts">
  import { urlFor } from "../../helpers";
  import { _ } from "../../i18n";
  import { HAVE_EXCEL } from "../../stores";

  export let query: string;

  /**
   * URL to download a query.
   */
  function queryUrl(query_string: string, format: string) {
    return urlFor(`download-query/query_result.${format}`, {
      query_string,
    });
  }
</script>

<span>
  ({_("Download as")}
  <a href={queryUrl(query, "csv")} data-remote>CSV</a>
  {#if $HAVE_EXCEL}
    ,
    <a href={queryUrl(query, "xls")} data-remote>XLS</a>
    ,
    <a href={queryUrl(query, "xlsx")} data-remote>XLSX</a>
    , or
    <a href={queryUrl(query, "ods")} data-remote>ODS</a>
  {/if}
  )
</span>

<style>
  span {
    color: var(--text-color-lighter);
  }
</style>
