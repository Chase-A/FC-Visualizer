<script>
	let ftemp = $state(70);
	let minTemp = -50;
	let maxTemp = 134;

	let descriptions = [
		"A cold day on the summit of Mt. Everest, Nepal",
		"So cold that it's recommended to stay inside",
		"Good conditions for skiing at your favorite mountain",
		"A cold rainy day, best to stay inside",
		"Cool and crisp, ideal weather for playing sports",
		"An average office's room temperature setting",
		"A warm day, perfect for enjoying the beach",
		"A heat wave, it's recommended to stay inside",
		"A hot day in Death Valley, California, USA"
	]
	let images = [
		"./everest.jpg",
		"./cold.jpg",
		"./ski.jpg",
		"./rain.jpg",
		"./footy.jpg",
		"./office.jpg",
		"./beach.jpg",
		"./hot.jpg",
		"./death_valley.jpg"
	]
</script>

<div class="body">
	<div class="app-container">
			{#if ftemp < -3} 
				<img class="photo" src={images[0]} alt="place where it's that hot">
				<p class="img-description">{descriptions[0]}</p>
			{:else if ftemp < 15}
				<img class="photo" src={images[1]} alt="place where it's that hot">
				<p class="img-description">{descriptions[1]}</p>
			{:else if ftemp < 32}
				<img class="photo" src={images[2]} alt="place where it's that hot">
				<p class="img-description">{descriptions[2]}</p>
			{:else if ftemp < 50}
				<img class="photo" src={images[3]} alt="place where it's that hot">
				<p class="img-description">{descriptions[3]}</p>
			{:else if ftemp < 65}
				<img class="photo" src={images[4]} alt="place where it's that hot">
				<p class="img-description">{descriptions[4]}</p>
			{:else if ftemp < 72}
				<img class="photo" src={images[5]} alt="place where it's that hot">
				<p class="img-description">{descriptions[5]}</p>
			{:else if ftemp < 90}
				<img class="photo" src={images[6]} alt="place where it's that hot">
				<p class="img-description">{descriptions[6]}</p>
			{:else if ftemp < 110}
				<img class="photo" src={images[7]} alt="place where it's that hot">
				<p class="img-description">{descriptions[7]}</p>
			{:else}
				<img class="photo" src={images[8]} alt="place where it's that hot">
				<p class="img-description">{descriptions[8]}</p>
			{/if}
	<div class="text-container">
		<p class="celcius">{Math.round((ftemp -32)* (5/9))}<span class="degrees">&deg;C</span></p>
		<p>{ftemp}<span class="degrees">&deg;F</span></p>
	</div>
	<input style="width: 100%; accent-color: #999" type="range" min={minTemp} max={maxTemp} bind:value={ftemp} />
</div>
</div>

<style>
	
	@import url('https://fonts.googleapis.com/css2?family=Reddit+Mono:wght@200..900&display=swap');


	.app-container {
		font-family: "Reddit Mono", monospace;
	}
	p {
		font-family: "Reddit Mono", monospace;
		font-size: 24px;
	}
	.text-container{
		display: flex;
		justify-content: space-between;
		margin: 0 auto;
		width: 70%;
		max-width: 250px;

	}
	.text-container p {
		font-family: "Reddit Mono", monospace;
		font-size: 64px;
		margin: 0;
		margin-bottom: 30px;
	}
	.text-container p .degrees {
		font-size: 24px;
		font-weight: 600px;
		vertical-align: top;
		position: relative;
		top: 12px;
	}
	.photo{
		width: 100%;
		max-width: 500px;
		margin: 0 auto;
		height: auto;
		animation: fadeIn 100ms linear forwards;
	}
	.img-description {
		font-size: 20px;
		text-align: center;
		max-width: 400px;
		margin: 20px auto;
	}
	@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>