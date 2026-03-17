---
title: Committing knowledge
type: 'split'
order: 10
---

<script>
	import LegacyTestCode from '$lib/demo/LegacyTestCode.svelte';
</script>

<div class="flex gap-8 h-full text-sm">
	<div class="flex-1 flex flex-col gap-4 text-gray-200 pt-1">
		<p>Sometimes Claude needs time to figure things out. Running two specific legacy-api tests was one of those — it spent about 5 minutes investigating, hitting dead ends, and eventually found the workaround entirely on its own.</p>
		<p>Once it does, don't let that knowledge disappear. Add it to CLAUDE.md so it never has to rediscover it.</p>
		<p class="text-gray-400">You can also just ask Claude to remember it: <span class="italic">"add this to the project CLAUDE.md"</span></p>
	</div>
	<div class="flex-1 h-full">
		<LegacyTestCode />
	</div>
</div>
