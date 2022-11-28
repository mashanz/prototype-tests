<script>
	let milestone_num = 0;
	let amount = 0;
	$: dates = [];
	$: percentage = `${100 / milestone_num} %`;
	$: amount_split = amount / milestone_num;

	function current_date(i, the_dates) {
		if (the_dates[i - 1]) {
			return new Date(
				new Date(the_dates[i - 1]).setDate(new Date(the_dates[i - 1]).getDate() + 1)
			)
				.toISOString()
				.slice(0, 10);
		} else {
			return new Date(Date.now()).toISOString().slice(0, 10);
		}
	}
</script>

<main class="flex h-screen w-full bg-gray-100">
	<div class="m-auto w-full max-w-2xl bg-white border p-2">
		<h1 class="font-bold text-xl pb-5">Transaction Milestone</h1>
		<form action="">
			<label for="milestone_num">Number of milestone</label>
			<input
				class="p-2 bg-gray-50 border mb-5 w-16"
				type="number"
				name="milestone_num"
				id="milestone_num"
				placeholder="1 to 100"
				max="100"
				min="1"
				required
				bind:value={milestone_num} />

			{#each { length: milestone_num } as _, i}
				<div class="grid grid-cols-4 gap-2">
					<div class="p-2">
						Milestone {i + 1}
					</div>
					<div>
						<input
							class="w-full p-2 border bg-gray-50"
							type="number"
							name="amount"
							id="amount"
							readonly
							bind:value={amount_split}
							disabled />
					</div>
					<div>
						<input
							class="w-full p-2 border bg-gray-50"
							type="text"
							name="percentage"
							id="percentage"
							readonly
							bind:value={percentage}
							disabled />
					</div>
					<div>
						<input
							class="w-full p-2 border bg-gray-50"
							type="date"
							name={'date_' + i}
							id={'date_' + i}
							min={current_date(i, dates)}
							bind:value={dates[i]} />
					</div>
				</div>
			{/each}

			<hr class="my-2" />

			<div class="grid grid-cols-4 gap-2">
				<div class="p-2">Total Payment Amount</div>
				<div>
					<input
						class="w-full p-2 border bg-gray-50"
						type="number"
						name="amount"
						id="amount"
						min="0"
						max="100000"
						required
						bind:value={amount} />
				</div>
				<div>
					<input
						class="w-full p-2 border bg-gray-50"
						type="text"
						name="percentage"
						id="percentage"
						value="100%" />
				</div>
				<div />
			</div>

			<div class="flex gap-2">
				<div class="flex-grow" />
				<button class="p-3 border border-blue-500 bg-white text-blue-500" type="reset">Back</button>
				<button class="p-3 border border-blue-500 bg-blue-500 text-white" type="submit">
					Next
				</button>
			</div>
		</form>
	</div>
</main>
