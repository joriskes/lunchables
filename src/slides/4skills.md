---
title: Skills
type: 'split'
order: 4
---

<script>
	import SkillCode from '$lib/demo/SkillCode.svelte';
</script>

<div class="flex gap-8 h-full text-sm">
	<div class="flex-1 flex flex-col gap-4 text-gray-200 pt-1">
		<p>Skills are reusable slash commands you invoke during a conversation:</p>
		<p class="text-yellow-300 bg-gray-800 rounded px-3 py-2 font-mono text-sm">/architect</p>
		<p>Each skill is a <code class="text-gray-400">SKILL.md</code> file inside a named directory. Two scopes:</p>
		<ul class="flex flex-col gap-2 ml-4 list-none">
			<li><strong class="text-white">Global</strong> — <code class="text-gray-400">~/.config/opencode/skills/architect/SKILL.md</code></li>
			<li><strong class="text-white">Per-project</strong> — <code class="text-gray-400">.opencode/skills/architect/SKILL.md</code></li>
		</ul>
		<p>Built-in skills:</p>
		<ul class="flex flex-col gap-2 ml-4 list-none">
			<li><code class="text-yellow-300">/simplify</code> — <span class="text-gray-300">reviews changed code for reuse, quality, and efficiency, then fixes issues found</span></li>
			<li><code class="text-yellow-300">/pr-review</code> — <span class="text-gray-300">reviews the current branch as a PR: checks for bugs, logic issues, security concerns, and code quality</span></li>
		</ul>
	</div>
	<div class="flex-1 h-full">
		<SkillCode />
	</div>
</div>
