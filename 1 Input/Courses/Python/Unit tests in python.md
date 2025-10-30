```
calculator.py

def main():
	x = input('x is')
	print('x squared is', square(x))
	
def square(n):
	return n * n
	
if __name__ == "__main__":
	main()
```

`pip install pytest`

```
test_calculator

import pytest
from calculator import square
	
def test_positive():
	assert square(2) == 4
	assert square(3) == 9
	
def test_negative():
	assert square(-2) == 4
	assert square(-3) == 9
	
def test_zero():
	assert square(0) == 0

def test_str():
	with pytest.raises(TypeError): // if we pass the string and TypeError raises
		square('cat')              // test is passed, cause code throw error
	
if __name__ == "__main__":
	main()
```

then run `pytest test_calculator.py`

If we put test file inside the folder, then create here `__init__.py` file, then `python` or `pytest` commands will understand that here we have executable when we will run 
`python test/pytest test`.

Links:

202510301704

