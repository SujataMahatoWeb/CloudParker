

<script runes>
	// ---------------- STATE ----------------
	let notes = $state([
		{ id: 1, title: 'Book 1', content: '' },
		{ id: 2, title: 'Book 2', content: '' }
	]);

	let activeNote = $state(notes[0]);
	let hoveredId = $state(null);
	let language = $state('HTML');

	// ---------------- FUNCTIONS ----------------
	function addNote() {
		const newNote = {
			id: Date.now(),
			title: 'New Note',
			content: ''
		};
		notes = [...notes, newNote];
		activeNote = newNote;
	}

	function deleteNote(id) {
		notes = notes.filter(n => n.id !== id);
		activeNote = notes[0] || null;
	}
</script>

<!-- ---------------- NAVBAR ---------------- -->
<nav class="shadow text-2xl py-3 px-4 flex gap-4 items-center">
	<img src="notepad-192.png" class="h-12" alt="Notepad" />
	<h1>NotePad</h1>
</nav>

<!-- ---------------- MAIN LAYOUT ---------------- -->
<div class="flex h-[calc(100vh-72px)]">

	<!-- ---------- LEFT : EXPLORER ---------- -->
	<div class="w-64 border-r p-3 bg-gray-50">
		<div class="flex justify-between items-center mb-3">
			<span class="font-semibold">Explorer</span>
			<button
				class="text-xl hover:text-blue-600"
				onclick={addNote}
			>
				＋
			</button>
		</div>

		{#each notes as note}
			<div
				class="flex justify-between items-center p-2 rounded cursor-pointer hover:bg-gray-200"
				on:click={() => (activeNote = note)}
				onmouseenter={() => (hoveredId = note.id)}
				onmouseleave={() => (hoveredId = null)}
			>
				<span class="truncate">📘 {note.title}</span>

				{#if hoveredId === note.id}
					<button
						class="text-red-500"
						onclick={(e) => {
							e.stopPropagation();
							deleteNote(note.id);
						}}
					>
						🗑️
					</button>
				{/if}
			</div>
		{/each}
	</div>

	<!-- ---------- RIGHT : EDITOR ---------- -->
	<div class="flex-1 p-4 flex flex-col">

		<!-- Language Tabs -->
		<div class="flex gap-2 mb-3">
			{#each ['HTML', 'CSS', 'JavaScript'] as lang}
				<button
					class="px-4 py-1 border rounded"
					class:bg-black={language === lang}
					class:text-white={language === lang}
					onclick={() => (language = lang)}
				>
					{lang}
				</button>
			{/each}
		</div>

		<!-- Editor -->
		{#if activeNote}
			<textarea
				class="flex-1 w-full border rounded p-3 font-mono focus:outline-none"
				bind:value={activeNote.content}
				placeholder="Write your notes or code here..."
			></textarea>
		{:else}
			<p class="text-gray-500">No note selected</p>
		{/if}

	</div>
</div>