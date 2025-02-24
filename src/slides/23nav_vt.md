---
title: Mobile Nav x Drawer
subtitle: View Transitions
type: 'demo'
order: 23
---

<script>
  import VTNav from '$lib/demo/VTNav.svelte'
</script>

<VTNav />

```html
<script>
	window.onload = function () {
		if (typeof window !== 'undefined') {
			const button = document.querySelector('button[popovertarget=demo-mobile-nav-vt]');
			const popover = document.querySelector('#demo-mobile-nav-vt');

			button.addEventListener('click', toggle);

			function toggle(e) {
				const is_opening = !popover.matches(':popover-open');
				e.preventDefault();
				document.startViewTransition(() => {
					if (is_opening) {
						return popover.showPopover();
					}
					return popover.hidePopover();
				});
			}

			document.addEventListener('keydown', (e) => {
				if (
					e.key === 'Escape' &&
					popover.hasAttribute('popover') &&
					popover.matches(':popover-open')
				) {
					toggle(e);
				}
			});
		}
	};
</script>

<button popovertarget="demo-mobile-nav-vt">NAV</button>

<nav popover id="demo-mobile-nav-vt">
	<button class="demo-button" popovertarget="demo-mobile-nav-vt" popovertargetaction="hide">
		Close Nav
	</button>
	<ul>
		<li><a href="#">Home</a></li>
		<li><a href="#">About</a></li>
		<li><a href="#">Store</a></li>
		<li><a href="#">Contact</a></li>
	</ul>
</nav>

<style>
	#demo-mobile-nav-vt[popover] {
		margin: 0;
		block-size: 100vb;
		inline-size: 40vw;
		inset-inline-start: unset;
		inset-inline-end: 0;
		view-transition-name: slide-mobile-nav-demo;
	}

	@keyframes slide-mobile-nav-demo {
		from {
			translate: 100vw;
		}
	}

	::view-transition-old(slide-mobile-nav-demo) {
		animation: 300ms ease-in reverse forwards slide-mobile-nav-demo;
	}

	::view-transition-new(slide-mobile-nav-demo) {
		animation: 300ms ease-out forwards slide-mobile-nav-demo;
	}
</style>
```
