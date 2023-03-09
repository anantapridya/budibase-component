<script>
  let options = [
    { label: "Option 1", value: 1 },
    { label: "Option 2", value: 2 },
    { label: "Option 3", value: 3 },
    { label: "Option 4", value: 4 },
    { label: "Option 5", value: 5 }
  ];
  let searchTerm = "";
  let selectedOptions = [];

  function filterOptions() {
    return options.filter(option =>
      option.label.toLowerCase().includes(searchTerm.toLowerCase())
    );
  }

  $: filteredOptions = filterOptions();
</script>

<input type="text" placeholder="Search options" bind:value={searchTerm} />

<select multiple bind:value={selectedOptions}>
  {#each filteredOptions as option}
    <option value={option.value}>{option.label}</option>
  {/each}
</select>

<!-- <style>
  .multiselect-container {
    position: relative;
    display: inline-block;
  }

  .multiselect-search {
    width: 100%;
    padding: 5px;
    margin-bottom: 5px;
    box-sizing: border-box;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 14px;
  }

  .multiselect-dropdown {
    position: absolute;
    top: 100%;
    left: 0;
    z-index: 1;
    min-width: 160px;
    padding: 5px;
    margin: 2px 0 0;
    list-style: none;
    background-color: #fff;
    border: 1px solid #ccc;
    border-radius: 4px;
    max-height: 200px;
    overflow-y: auto;
  }
</style> -->