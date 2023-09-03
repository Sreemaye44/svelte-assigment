<script>
    import { onMount } from 'svelte';
  import { countryDataStore } from '../../stores/countryDataStore';

  const data = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]; // Replace with your data

   onMount(async () => {
    try {
      const response = await fetch('https://restcountries.com/v3.1/all');
      const data = await response.json();
      countryDataStore.set(data);
    } catch (error) {
      console.error('Error fetching country data:', error);
    }
  },);
  
  console.log(countryDataStore);


</script>

<div class="flex justify-between p-16">
  <div class="w-9/12 me-5">
   <table class="table w-full border">
     <thead>
            <tr>
                <th>Flag</th>
                <th>Name</th>
                <th>Population</th>
                <th>CIOC</th>
                <th>UN Member Status</th>
                <th>Currecies</th>
                <th>Languages</th>
            </tr>
        </thead>
        <tbody>

  <!-- Use data from the store -->
  {#if $countryDataStore}
    {#each $countryDataStore as country}
      
        <tr>
            <td>{country.flag}</td>
            <td>{country.name.common}</td>
            <td>{country.population}</td>
            <td>{country.cioc}</td>
            <td><button class="btn">{country.unMember? 'Yes':'No'}</button></td>
            {#each Object.keys(country.currencies) as key}
            <td>{[key]}</td>
            {/each}
            {#each Object.keys(country.languages) as key}
            <td>{country.languages[key]}</td>
            {/each}
        </tr>
        
    {/each}
  {/if}
  </tbody>
     </table>
</div>

</div>