# DuckDuckGo

[DuckDuckGo](https://duckduckgo.com/) is an internet search engine that emphasizes protecting searchers' privacy and avoiding the filter bubble of personalized search results. DuckDuckGo does not show search results from content farms.

Much like google, DuckDuckGo supports some nice operators:

| Operator Example | Result |
| :--- | :--- |
| `cats dogs` | Results about cats or dogs |
| `"cats and dogs"` | Results for exact term "cats and dogs". If no results are found, we'll try to show related results. |
| `cats -dogs` | Fewer dogs in results |
| `cats +dogs` | More dogs in results |
| `cats filetype:pdf` | PDFs about cats. Supported file types: pdf, doc\(x\), xls\(x\), ppt\(x\), html |
| `dogs site:example.com` | Pages about dogs from example.com |
| `cats -site:example.com` | Pages about cats, excluding example.com |
| `intitle:dogs` | Page title includes the word "dogs" |
| `inurl:cats` | Page url includes the word "cats" |

{% hint style="info" %}
DuckDuckGo has a really neat feature. When you submit a search, preface your search term with a `\` to jump immediately to the first result of the search. For example, `\"Rick and Morty"`
{% endhint %}

