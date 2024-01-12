<svelte:head>
	<title>About</title>
	<meta name="description" content="About this app" />
</svelte:head>

<script>
	import { onMount } from "svelte";

	// MathJax = {
	// 	tex: {
	// 		inlineMath: [
	// 			['$', '$'],
	// 			['\\(', '\\)']
	// 		]
	// 	}
	// };
	let var1 = `$P_{i}$`
	let var2 = `$i$`
	let var3 = `$T_{n}$`
	let var4 = `$T_{d}$`

	let equ1 = `$$T=\\sum_{i}P_{i}$$`;
	let equ2 = `$$\\text{Percentage of item }i = \\frac{P_{i}}{T_{n}}$$`;
	let equ3 = `$$\\text{Value of item } i=\\text{Percentage of item } i×T_{d}$$`;

	onMount(() => {
		let script = document.createElement('script');
    script.src = "https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js";
    document.head.append(script);
		
		script.onload = () => {
      MathJax = {
        tex: {inlineMath: [['$', '$'], ['\\(', '\\)']]},
        svg: {fontCache: 'global'}
      };
		};
	})
</script>


<div class="text-column">
	<h1>About this app</h1>

	<p>This app was inspired by how my friends split the bill whenever we order food online together. </p>

	<p>Let {var1} represent the regular price of item {var2}, {var3} represent the total sum of all regular prices, and {var4} represent the price total amount after discounts. In general, the steps are as follows:</p>
	
	<ol>
		<li>
			Begin by adding up all the regular prices of the items on the bill.
			<br>
			{equ1}
		</li>
		<li>
			Calculate the percentage each item contributes to the total sum by dividing its individual price by the overall sum.
			<br>
			{equ2}
		</li>
		<li>
			Once you have the percentage for each item, apply these percentages to the total bill amount after any discounts have been applied. This will determine the specific value each item holds in the discounted total.
			{equ3}
		</li>
	</ol>

	<p></p>
</div>

<style>
	li {
		margin-bottom: 8px;
	}

	*:not(:last-child):not(li) {
		margin-top: 0;
		margin-bottom: 16px;
	}
</style>