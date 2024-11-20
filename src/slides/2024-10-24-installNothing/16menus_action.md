---
title: Menus x Popovers
subtitle: Popover Actions
type: 'demo'
order: 16
---

<script>
  import ActionPopover from '$lib/demo/2024-10-24-installNothing/ActionPopover.svelte'
</script>

<ActionPopover />

```html
<button popovertargetaction="show" popovertarget="ampd">Show</button>

<div popover id="ampd" class="menu">
	<button popovertargetaction="hide" popovertarget="ampd">Hide</button>
</div>
```
