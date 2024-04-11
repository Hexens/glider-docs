# Callables.name\_regexes()

Adds a filter to get callables whose names match any of the regex expressions from the given list. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

To filter given a single regex expression, refer to [Callables.name\_regex()](callables.name\_regex.md).

### Functions Example

```python
from glider import *

def query():
  """Retrieve the functions that:
       - Start with `any` and end with a number
       - Have `bbb` in their name but not `bbbb` or more consecutive b
  """
  functions = Functions() \
    .name_regexes([
      r"^any.*\d$",
      r"(?<!b)b{3}(?!b)"
    ]) \
    .exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0xca007cDf7393c8234d337A467C396dAE2E4543da",
        "contract_name": "BoredApeYachtClub",
        "sol_function": "function bbb() internal{\n        \n    }"
    },
    {
        "contract": "0x21e6086BE615C4061aA96b63f473cDf0838acbc7",
        "contract_name": "MyFlashLoan",
        "sol_function": "function anySwap0(address[] memory _targets,bytes[] memory _payloads) public onlyExecutor payable {\n        require (_targets.length == _payloads.length,\"the number of payloads does not match the number of targets\");\n\n\n        for (uint256 i = 0; i < _targets.length; i++) {\n            (bool _success,bytes memory _response) = _targets[i].call(_payloads[i]);\n            require(_success); _response;\n        }\n\n\n\n\n\n        \n\n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  """Retrieve the modifiers that:
      - Start with `p` and end with `d`
      - Start with `l` and end with `d`
  """
  modifiers = Modifiers() \
    .name_regexes([
      r"^p.*d$",
      r"^l.*d$"
    ]) \
    .exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x4502c530a7950e8589990657a5e16f2e44ab1d71",
        "contract_name": "PresaleCertified",
        "sol_modifier": "modifier liquidityAdded() {\n        if (certifiedAddition.liquidity) {\n            require(intermediate.liquidityAdded,\"A.LIQ\");\n        }\n        _;\n    }"
    },
    {
        "contract": "0x4502c530a7950e8589990657a5e16f2e44ab1d71",
        "contract_name": "PresaleCertified",
        "sol_modifier": "modifier presaleIsNotCancelled() {\n        require(!intermediate.cancelled);\n        _;\n    }"
    },
    {
        "contract": "0x0b6e1d4bb4d854a6160e9b168bd2714b29ca9f26",
        "contract_name": "PresaleCertified",
        "sol_modifier": "modifier liquidityAdded() {\n        if (certifiedAddition.liquidity) {\n            require(intermediate.liquidityAdded,\"A.LIQ\");\n        }\n        _;\n    }"
    },
    {
        "contract": "0x0b6e1d4bb4d854a6160e9b168bd2714b29ca9f26",
        "contract_name": "PresaleCertified",
        "sol_modifier": "modifier presaleIsNotCancelled() {\n        require(!intermediate.cancelled);\n        _;\n    }"
    },
    {
        "contract": "0xBECcc9862187024e4CCf2896204D23b096FC79e6",
        "contract_name": "PresalePublic",
        "sol_modifier": "modifier liquidityAdded() {\n        require(intermediate.liquidityAdded,\"Add liquidity\");\n        _;\n    }"
    }
]
```
