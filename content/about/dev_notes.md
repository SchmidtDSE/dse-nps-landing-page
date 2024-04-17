---
title: Developer Notes
type: docs
prev: docs/folder/
weight: 4
---

- Pages take a few seconds to load upon changing pages - this is expected
- Especially on first map view, the burn metrics may take several seconds to render properly. This can typically be resolved by refreshing the page, or switching between the `Continious` and `Categorical` burn severity layer, which will trigger a re-render.
- The combinaton of `Fire Event Name` and `Affiliation` _must be unique_. If you re-submit a request using the same `Fire Event Name` and `Affiliation`, you will overwrite the existing products within the server. Please feel free to do so if you've made a mistake or if you are experimenting!
- Within the map view, the left side legend may be obscured on some screens - this may occur if your burn area is sufficently rich with cover type information and is a known issue. You may be able to resolve this by zooming out within your browser.

If something breaks, or otherwise goes awry, we will receive logs of your session and will hopefully be able to resolve your issue - feel free to reach out to [mweltman-fahs@berkeley.edu](mailto:mweltman-fahs@berkeley.edu) and/or [npg@berkeley.edu](mailto:npg@berkeley.edu) with any additional context you think may be useful!
