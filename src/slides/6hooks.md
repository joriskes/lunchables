---
title: Formatters & Plugins
type: 'split'
order: 6
---

<script>
	import HooksCode from '$lib/demo/HooksCode.svelte';
</script>

<div class="flex gap-8 h-full text-sm">
	<div class="flex-1 flex flex-col gap-4 text-gray-200 pt-1">
		<p>After every file write, OpenCode checks for a matching formatter and runs it automatically — no instruction to the LLM needed.</p>
		<p>Built-in formatters activate when the right tool is present: <code class="text-gray-400">prettier</code> if it's in <code class="text-gray-400">package.json</code>, <code class="text-gray-400">pint</code> if <code class="text-gray-400">laravel/pint</code> is in <code class="text-gray-400">composer.json</code>, and so on.</p>
		<p>For anything else — like running <code class="text-yellow-300 bg-gray-800 px-1 rounded">php-cs-fixer</code> inside a docker container — you define a custom formatter in <code class="text-gray-400">opencode.json</code>.</p>
		<ul class="flex flex-col gap-1 ml-4 list-disc text-gray-300">
			<li>Plugins for broader automation: notifications, .env protection, custom tools</li>
		</ul>
		<p class="text-gray-500 text-xs">Note: this formatter calls into a docker container — more on that setup in the next slides.</p>
	</div>
	<div class="flex-1 h-full">
		<HooksCode />
	</div>
</div>
