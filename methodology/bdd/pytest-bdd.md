# Pytest BDD

## Parsers 

##  String

Noop, works as strict comparison

##  Parse

Extended parser that allow to use syntax like this:

```python

'{myParam:MyType}'

```

## Cfparse

Extension of *Parse* with cardinality field (CF) support based on regexp syntax.

```python

'{myParam:MyType+}' # like 1..N

'{myParam:Mytype?}' # like 0..1

'{myParam:MyType*}' # like 0..N

```

```python

@given(parsers.cfparse('{myParam:String}, world!', extra_types=dict(
    String=str
)))

```


## re


Uses Regexp for parsing step. Need named groups in order to define variables.

```python

@given(parsers.re(r'(?P<something>\w+), world!', converters=dict(
    something=str
)))

```

## Step aliases

*Pytest-bdd* has ability to set aliases for the step

```python

@given('My first sttep alias')
@given('Yet another step alias')
def myStep(par1):
    return smth()

```

## Step scope execution

*Pytest-bdd* has ability to set scope execution up. 

```python

@given('My super step', scope='session')
def test_step():
    pass

```

## Override fixtures

```python

import pytest
from pytest_bdd import given, then

@pytest.fixture
def foo():
    return "foo"

@given('Invoke fixture injection', target_fixture='foo')
def foo_inject():
    return 'bar'

```

## Multiline steps support 

```

Scenario: My mulitiline scenario
   Given My first step with
       more lines
       and more lines
       and it is good qusetion
       about formatting of it
    Then we have single scinario with multiline content

```

## 


