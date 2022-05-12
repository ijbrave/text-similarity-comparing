<script>
	import stringSimilarity from 'string-similarity'

	let similarity = 0

	let text1 = ''
	let text2 = ''

	$: similarityPercentage = (similarity * 100).toFixed(2)
</script>

<main>
	<h1><bold>{similarityPercentage}%</bold> :درصد تشابه</h1>
	<div class="container">
		<div class="input-container">
			<textarea
				dir="auto"
				placeholder="متن اول"
				bind:value={text1}
				on:input={() => {
					similarity = stringSimilarity.compareTwoStrings(text1, text2)
				}}
			/>
		</div>
		<div class="input-container">
			<textarea
				dir="auto"
				placeholder="متن دوم"
				bind:value={text2}
				on:input={() => {
					similarity = stringSimilarity.compareTwoStrings(text1, text2)
				}}
			/>
		</div>
	</div>
</main>

<style>
	:root {
		font-family: Vazirmatn, sans-serif;
		font-size: 1rem;
		background-color: #202142;
	}

	main {
		max-width: 968px;
		margin: 6rem auto;
		padding: 0.5rem;
		text-align: center;
		border-radius: 0.5rem;
		background-color: #fff;
	}

	h1 {
		font-size: 2.8rem;
		color: #202142;
	}

	bold {
		color: #ff6a95;
	}

	.container {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
	}
	.input-container {
		display: flex;
		flex: 50%;
		flex-direction: column;
		justify-content: center;
	}

	textarea {
		font-family: Vazirmatn, sans-serif;
		height: 16rem;
		margin: 0 0.8rem;
		margin-bottom: 2rem;
		padding: 0.5rem;
		border-radius: 0.4rem;
		font-size: 1rem;
		border: 1px solid #202142;
	}
	textarea:focus {
		outline: none;
		border: 1px solid #ff6a95;
	}

	textarea::placeholder {
		text-align: right;
	}

	@media only screen and (max-width: 40em) {
		main {
			margin: 4rem 0.8rem;
		}
	}

	@media only screen and (max-width: 30em) {
		main {
			margin: 2rem 0.5rem;
		}
		textarea {
			height: 10rem;
		}
		h1 {
			font-size: 2rem;
		}
	}
</style>
