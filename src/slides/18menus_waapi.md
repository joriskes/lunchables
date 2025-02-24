---
title: Menus x Popovers
subtitle: WAAPI & JS Anchor
type: 'demo'
order: 18
---

<script>
  import WaapiPopover from '$lib/demo/WaapiPopover.svelte'
</script>

<WaapiPopover />

```html
<button popovertargetaction="show" popovertarget="ampd">Show</button>
<script>
	window.onload = function () {
		if (typeof window !== 'undefined') {
			let button = document.getElementById('md');
			let popover = document.getElementById('mdp');

			button.addEventListener('click', toggle);

			function update_position() {
				const target_position = button.getBoundingClientRect();
				popover.style.inset = 'unset';
				popover.style.top = target_position.bottom + 'px';
				popover.style.left = target_position.right - target_position.width + 'px';
			}
			const resizeObserver = new ResizeObserver(update_position);
			resizeObserver.observe(popover);
			window.addEventListener('resize', update_position);
			window.addEventListener('scroll', update_position);

			// Animation
			function toggle() {
				const is_opening = !popover.matches(':popover-open');
				const translate = is_opening ? ['0 10px', '0 0'] : ['0 0', '0 10px'];
				const opacity = is_opening ? [0, 1] : [1, 0];

				if (is_opening) popover.showPopover();

				window.requestAnimationFrame(() => {
					let animation = popover.animate(
						{
							translate,
							opacity
						},
						{
							duration: 300,
							easing: 'ease-in-out',
							fill: 'forwards'
						}
					);
					animation.onfinish = () => {
						if (!is_opening) popover.hidePopover();
					};
				});
			}

			// In Manual mode, you need to trigger keyboard events yourself
			document.addEventListener('keydown', (event) => {
				if (
					event.key === 'Escape' &&
					popover.hasAttribute('popover') &&
					popover.matches(':popover-open')
				) {
					toggle();
				}
			});
		}
	};
</script>

<button id="md" class="menu-button"><img src="/menu.svg" /></button>
<!-- Note: Manual Mode Required -->
<div popover="manual" id="mdp" class="menu">
	<ul class="menu-demo">
		<li><a href="#">Settings</a></li>
		<li><a href="#">My Profile</a></li>
		<li><a href="#">Help</a></li>
		<li><a href="#">Logout</a></li>
	</ul>
</div>
```
