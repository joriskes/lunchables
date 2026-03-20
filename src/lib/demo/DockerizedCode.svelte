<script lang="ts">
	const code = `## Weeztix Development Environment
All Weeztix services run via docker-compose,
managed by the \`dockerized\` tool at
\`~/eventix/dockerized\`.

### e* aliases
Running \`eval "$(~/eventix/dockerized/dockerized aliases)"\`
sets up context-aware aliases. When run from
inside a repo directory, each alias finds the
running container with that path mounted and
either \`docker exec\`s in or starts a fresh one.

| Alias      | Runs                              |
|------------|-----------------------------------|
| \`ephp\`     | \`php\` in PHP container            |
| \`ephpunit\` | \`phpunit\` in PHP container        |
| \`eyarn\`    | \`yarn\` in Node container          |
| \`enode\`    | \`node\` in Node container          |
| \`ego\`      | \`go\` in Go container              |
| \`esh\`      | \`sh\` exec into running container  |

### Useful env vars

- \`NO_TTY=true\` — skip the \`-it\` flag;
  required when running from a
  non-interactive context (e.g. OpenCode)
- \`NEW_CONTAINER=true\` — force a fresh
  container
- \`PRINT_COMMAND=true\` — print the full
  docker command before running

### Running tests

- PHP: \`cd\` into the repo, run \`ephpunit\`
- Go: \`cd\` into the repo, run \`ego test ./...\`
- Node: \`cd\` into the repo, run \`eyarn test\``;

	function esc(str: string): string {
		return str.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;');
	}

	function highlight(raw: string): string {
		return raw
			.split('\n')
			.map((line) => {
				if (line.startsWith('## ')) return `<span class="h2">${esc(line)}</span>`;
				if (line.startsWith('### ')) return `<span class="h3">${esc(line)}</span>`;
				if (line.startsWith('- ')) {
					const inner = esc(line.slice(2)).replace(/`([^`]+)`/g, '<span class="code">$1</span>');
					return `<span class="bullet-marker">- </span><span class="text">${inner}</span>`;
				}
				if (line.startsWith('|')) {
					const inner = esc(line).replace(/`([^`]+)`/g, '<span class="code">$1</span>');
					return `<span class="table">${inner}</span>`;
				}
				if (line.trim() === '') return '';
				const inner = esc(line).replace(/`([^`]+)`/g, '<span class="code">$1</span>');
				return `<span class="text">${inner}</span>`;
			})
			.join('\n');
	}
</script>

<pre
	class="h-full overflow-y-auto rounded-lg p-4 text-xs leading-relaxed bg-[#0d1117] font-mono">{@html highlight(
		code
	)}</pre>

<style>
	pre :global(.h2) {
		color: #61afef;
		font-weight: bold;
	}
	pre :global(.h3) {
		color: #56b6c2;
		font-weight: bold;
	}
	pre :global(.bullet-marker) {
		color: #56b6c2;
	}
	pre :global(.code) {
		color: #e5c07b;
	}
	pre :global(.table) {
		color: #5c6370;
	}
	pre :global(.text) {
		color: #abb2bf;
	}
	pre {
		color: #abb2bf;
	}
</style>
