# Deep Copy
```python
a = b[:] # copies contents of b to a
# problem: this is not a deep copy
# solution: import deep copy
a = [1, 2, [3, 4]]
# a[3] copied is a reference
from copy import deepcopy
b = deepcopy(a)
```

# Pandas
- You can't see the intermediate state for Groupby
- Pandas groupby will operate on columns that have meaning.
- Max will keep all of the values, sum will only keep the values you groupby with. Diff will keep everything
- Pandas has a concept of index, multilayered index allows you to manipulate columns and assign it to a new column

## Merge
- You can merge 2 dataframes by providing which column you want to merge it on
- The result can be from 0 - len(df1) * len(df2)
- Result will always be a dataframe
- If you want to merge, but you don't want to lose data, you use how='left'
