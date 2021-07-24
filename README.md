# Session 11 Readme file.

### Only the difference in the code from previous week's assignment are shown!

## Link to Colab file

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1HDZXrZWosuFjcQsslqW3f_WSf98aZo2Q?usp=sharing)

## Objective
The objective of this assignmnet is to turn our Polygon Sequence Class (from last week's assignmnet) into an iterator and iterable


## Iterator and Iterable
### Difference
The main difference is that an iterator gets exhausted whereas an iterable does NOT get exhausted!

### Requirements for an Iterable
- An `__iter__` method, which returns an iterator


### Requirements for an Iterator

- An `__iter__` method, which returns an iterator
- A(n) `__next__` method, which must be defined on the iterator
	- A StopIteration execution inside the `__next__` method, which will let a loop know the end of the iterations


### Summary
| Field  | Iterator | Iterable |
| ------------- | ------------- |------------- |
| `__iter__`  | YES  | YES |
| `__next__`  | YES  | OPTIONAL |
| `__getitem__`  | OPTIONAL  | OPTIONAL |

### Modifications Made
Since we are required to make it both iterator and iterable we will define the following things
- an iterator Class (called as `PolySeqIter` inside the `PolySeq` Class); this sub-class will have its own `__iter__` method (to return itself) and the `__next__` method.
- an `__iter__` method that returns the sub-class `PolySeqIter`



## Task


First, the `__iter__` method is implemented, which returns an iterator that has been implemented as a sub-class

```python
def __iter__(self):
        '''
        This method was added for this week's asignment. It returns the iterator sub-class
        '''
        return self.PolySeqIter(self)
```


The iterator

```python
class PolySeqIter:
	'''
	This is an iterator implemented as a sub-class
	'''

	def __init__(self, poly):
		self.poly = poly
		self.i = 0

	def __iter__(self):
		return self

	def __next__(self):
		if self.i >= len(self.poly):
			raise StopIteration
		else:
			item = self.poly.polygons[self.i]
			self.i += 1
			return item
```
