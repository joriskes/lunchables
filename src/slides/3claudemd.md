---
title: CLAUDE.md
type: 'split'
order: 3
---

<script>
	import ClaudeMemoryCode from '$lib/demo/ClaudeMemoryCode.svelte';
</script>

<div class="flex gap-8 h-full text-sm">
	<div class="flex-1 flex flex-col gap-4 text-gray-200 pt-1">
		<p>Claude reads <code class="text-yellow-300 bg-gray-800 px-1 rounded">CLAUDE.md</code> at the start of <em>every</em> conversation.</p>
		<p>Two scopes:</p>
		<ul class="flex flex-col gap-2 ml-4 list-none">
			<li><strong class="text-white">Global</strong> — <code class="text-gray-400">~/.claude/CLAUDE.md</code><br/><span class="text-gray-400 text-xs">Applies to all projects</span></li>
			<li><strong class="text-white">Per-project</strong> — <code class="text-gray-400">CLAUDE.md</code> at repo root<br/><span class="text-gray-400 text-xs">Checked into git, shared with the team</span></li>
		</ul>
		<p>Don't want to write it yourself? Run <code class="text-yellow-300 bg-gray-800 px-1 rounded">/init</code> — Claude will analyse the codebase and generate one for you.</p>
		<p>Use it to encode:</p>
		<ul class="flex flex-col gap-1 ml-4 list-disc text-gray-300">
			<li>Tone &amp; communication style</li>
			<li>Coding conventions</li>
			<li>Tooling context (how to run tests, docker setup, etc.) <span class="text-gray-500">— more on this later</span></li>
			<li>Hard rules (never force push, always ask before deleting)</li>
		</ul>
	</div>
	<div class="flex-1 h-full">
		<ClaudeMemoryCode />
	</div>
</div>
