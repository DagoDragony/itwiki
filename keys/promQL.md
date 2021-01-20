promQL

```
sum by(__name__)({tenant="Team Data Products"}) # all metrics
count({tenant="Team Data Products"}) by (job)   # get unique labels
```
