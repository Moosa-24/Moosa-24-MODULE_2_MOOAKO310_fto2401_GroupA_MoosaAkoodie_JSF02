<script>
    /**
   * Main layout for the product page.
   * Includes filters, sorting options, and the product list.
   */
    import ProductList from '../Product/ProductList.svelte';
    import Filter from '../components/Filter.svelte';
    import Sort from '../components/Sort.svelte';
  </script>
  
  <div class="grid lg:flex gap-y-4 gap-x-48 lg:items-start mt-3 mx-auto justify-center">
    <Filter />
    <Sort />
  </div>
  <ProductList />
  
  <style>
    
  </style>
  