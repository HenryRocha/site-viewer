<script lang="ts">
	type View = {
		url: string;
		title: string;
		element_id: string;
	};

	let views: Array<View> = [];
	add_view();

	function add_view() {
		views.push({
			url: 'https://en.wikipedia.org/wiki/Lorem_ipsum',
			title: 'Lorem Ipsum',
			element_id: crypto.randomUUID().toString()
		});
		views = views;
	}

	function remove_view(vi: number) {
		views.splice(vi, 1);
		views = views;
	}

	function reload_view(vi: number) {
		views[vi].url += '';
		views = views;
	}

	function print_view(vi: number) {
		// API call to generate PDF.
	}
</script>

<div class="flex flex-row gap-4 px-4 py-2 place-content-end">
	<button type="button" class="btn-icon btn-icon-lg variant-filled" on:click={add_view}>
		<svg
			xmlns="http://www.w3.org/2000/svg"
			fill="none"
			viewBox="0 0 24 24"
			stroke-width="1.5"
			stroke="currentColor"
			class="w-6 h-6"
		>
			<path stroke-linecap="round" stroke-linejoin="round" d="M12 4.5v15m7.5-7.5h-15" />
		</svg>
	</button>
</div>

<div class="snap-x scroll-px-4 snap-mandatory scroll-smooth flex gap-4 overflow-x-auto px-4 w-100">
	{#each views as view, i}
		<div class="snap-center shrink-0 grow">
			<div class="card">
				<header class="card-header">
					<div class="flex flex-row gap-4 place-content-between items-center">
						<div class="flex-grow">
							<input
								class="input"
								title={view.url}
								type="text"
								placeholder={view.url}
								bind:value={view.url}
							/>
							<!-- <h1 class="h1">
								{view.title}
							</h1> -->
						</div>

						<div>
							<button
								type="button"
								class="btn-icon btn-icon-lg variant-filled"
								on:click={() => reload_view(i)}
							>
								<svg
									xmlns="http://www.w3.org/2000/svg"
									fill="none"
									viewBox="0 0 24 24"
									stroke-width="1.5"
									stroke="currentColor"
									class="w-6 h-6"
								>
									<path
										stroke-linecap="round"
										stroke-linejoin="round"
										d="M16.023 9.348h4.992v-.001M2.985 19.644v-4.992m0 0h4.992m-4.993 0l3.181 3.183a8.25 8.25 0 0013.803-3.7M4.031 9.865a8.25 8.25 0 0113.803-3.7l3.181 3.182m0-4.991v4.99"
									/>
								</svg>
							</button>

							<button
								type="button"
								class="btn-icon btn-icon-lg variant-filled"
								on:click={() => print_view(i)}
							>
								<svg
									xmlns="http://www.w3.org/2000/svg"
									fill="none"
									viewBox="0 0 24 24"
									stroke-width="1.5"
									stroke="currentColor"
									class="w-6 h-6"
								>
									<path
										stroke-linecap="round"
										stroke-linejoin="round"
										d="M6.72 13.829c-.24.03-.48.062-.72.096m.72-.096a42.415 42.415 0 0110.56 0m-10.56 0L6.34 18m10.94-4.171c.24.03.48.062.72.096m-.72-.096L17.66 18m0 0l.229 2.523a1.125 1.125 0 01-1.12 1.227H7.231c-.662 0-1.18-.568-1.12-1.227L6.34 18m11.318 0h1.091A2.25 2.25 0 0021 15.75V9.456c0-1.081-.768-2.015-1.837-2.175a48.055 48.055 0 00-1.913-.247M6.34 18H5.25A2.25 2.25 0 013 15.75V9.456c0-1.081.768-2.015 1.837-2.175a48.041 48.041 0 011.913-.247m10.5 0a48.536 48.536 0 00-10.5 0m10.5 0V3.375c0-.621-.504-1.125-1.125-1.125h-8.25c-.621 0-1.125.504-1.125 1.125v3.659M18 10.5h.008v.008H18V10.5zm-3 0h.008v.008H15V10.5z"
									/>
								</svg>
							</button>

							<button
								type="button"
								class="btn-icon btn-icon-lg variant-filled"
								on:click={() => remove_view(i)}
							>
								<svg
									xmlns="http://www.w3.org/2000/svg"
									fill="none"
									viewBox="0 0 24 24"
									stroke-width="1.5"
									stroke="currentColor"
									class="w-6 h-6"
								>
									<path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
								</svg>
							</button>
						</div>
					</div>
				</header>

				<section class="p-4">
					<iframe
						class="min-h-a4 h-a4 min-w-a4 w-full"
						frameborder="0"
						id={view.element_id}
						src={view.url}
						title={view.title}
					/>
				</section>

				<!-- <footer class="card-footer">(footer)</footer> -->
			</div>
		</div>
	{/each}
</div>
