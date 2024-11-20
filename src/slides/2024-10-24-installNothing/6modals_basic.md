---
title: Modals x Alerts x Dialogs
subtitle: Basic Modal
type: 'demo'
order: 6
---

<script>
  import BasicDialog from '$lib/demo/2024-10-24-installNothing/BasicModal.svelte'
</script>

<BasicDialog />

```html
<script>
	window.onload = function () {
		if (typeof window !== 'undefined') {
			const trigger = document.querySelector('#demo-modal-open');
			const dialog = document.querySelector('#demo-modal');
			trigger.addEventListener('click', () => {
				dialog.showModal();
			});
		}
	};
</script>

<button id="demo-modal-open">Open</button>
<dialog id="demo-modal">
	<p>Login</p>
	<form method="dialog">
		<input type="text" placeholder="username" />
		<input type="password" placeholder="password" />
		<button type="submit">Login</button>
	</form>
</dialog>
```
