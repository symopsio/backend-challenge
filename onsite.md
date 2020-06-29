# Sym Backend Onsite

You will pair with your interviewer to extend your coding challenge submission with the following features.

## Crawl

We want to implement a simple web crawler over our registry of URLs. `msr crawl` should visit each URL in the registry, crawling linked pages recursively to a configurable depth (`--depth`), which defaults to 3.

The crawler should cache the contents of pages which have already been crawled, so as to avoid extraneous requests across calls to `crawl`, in an LRU cache that keeps keys for at at most $min(\text{MaxAge}_s, \text{30 minutes})$, where $\text{MaxAge}_s$ is specified by the `Cache-Control` header, if present, for site $s$.

The crawler should build up a graph as it crawls, to avoid loops and unnecessary requests within a given call to `crawl`. You may use any graph search algorithm to accomplish this. This graph should be persisted before the call to `crawl` terminates.

The output of the `crawl` command should be a summary table of the number of URLs crawled, and any URLs that resulted in an error. The crawl graph should also be persisted, so it can be utilized in future commands.

## Rank

`msr rank` should traverse the most recently-persisted `crawl` graph, run the [PageRank](https://en.wikipedia.org/wiki/PageRank) algorithm, and return the $N$ URLs with the highest PageRank. $N$ defaults to 5, can can be configured with the `-n` flag.

<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
      inlineMath: [['$','$']]
    }
  });
</script>
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
