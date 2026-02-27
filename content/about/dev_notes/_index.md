---
title: Developer Updates
---

This section contains information about the development of the tool, including updates, known issues, and other relevant information. We will make every effort to keep this page up-to-date.

### Known bugs:

- None at this time!

### Known issues:

{{< callout type="warning" >}}
Especially on first map view, the burn metrics may take several seconds to render properly. This can typically be resolved by refreshing the page, or switching between the `Continuous` and `Categorical` burn severity layer, which will trigger a re-render. Additionally, the burn severity layers are not checked by default, you will need to check one of `Continuous` or `Categorical` to see the burn severity metrics.
{{< /callout >}}

{{< callout type="warning" >}}
Very large fires suffer some performance limitations, and may not render properly within the tool. If you are having issues with your analysis, please reach out to [npg@berkeley.edu](mailto:npg@berkeley.edu) for assistance.
{{< /callout >}}

### Known limitations:

{{< callout type="info" >}}

Pages take a few seconds to load upon changing pages - this is expected
{{< /callout >}}

{{< callout type="info" >}}

The combination of `Fire Event Name` and `Affiliation` _must be unique_. If you re-submit a request using the same `Fire Event Name` and `Affiliation`, you will overwrite the existing products within the server. You may do so if you have made a mistake or wish to experiment.

{{< /callout >}}

If you encounter an issue, we will receive logs of your session and will work to resolve it. Please reach out to [mweltman-fahs@berkeley.edu](mailto:mweltman-fahs@berkeley.edu) and/or [npg@berkeley.edu](mailto:npg@berkeley.edu) with any additional context you think may be useful.
