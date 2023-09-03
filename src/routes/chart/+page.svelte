<script>
	// @ts-nocheck

	import { onMount } from "svelte";
	import { countryDataStore } from "../../stores/countryDataStore";
	import { sortedPopulationStore } from "../../stores/sortedPopulationStore";
	import RightChart from "./RightChart.svelte";
	// Replace with your data

	onMount(async () => {
		try {
			const response = await fetch("https://restcountries.com/v3.1/all");
			const data = await response.json();
			const sortedData = data
				.sort((a, b) => b.population - a.population)
				.slice(0, 10);
			countryDataStore.set(data);
      sortedPopulationStore.set(sortedData);
		} catch (error) {
			console.error("Error fetching country data:", error);
		}
	});
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
				{#each $countryDataStore as country}
					<tr>
						<td><img src={country.flags.svg} alt="" class="h-12 w-12" /></td>
						<td>{country.name.common}</td>
						<td>{country.population}</td>
						<td>{country.cioc}</td>
						<td>
							<button class="btn">{country.unMember ? "Yes" : "No"}</button>
						</td>
						<td>
							{#each Object.keys(country.currencies) as key, i}
								{(i > 0 || i < Object.keys(country.currencies).length - 1
									? ", "
									: "") + [key]}
							{/each}
						</td>
						<td>
							{#each Object.keys(country.languages) as key, i}
								{(i > 0 || i < Object.keys(country.currencies).length - 1
									? ", "
									: "") + country.languages[key]}
							{/each}
						</td>
					</tr>
				{/each}
			</tbody>
		</table>
	</div>
  <RightChart/>
</div>
