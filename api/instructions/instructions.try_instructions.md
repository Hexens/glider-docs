# Instructions.try\_instructions()

Returns an [Instructions](./) object for the 'try' instructions.

`try_instructions() →` [`Instructions`](./)

## Query Example

<pre class="language-python"><code class="lang-python"><strong>from glider import *
</strong>
def query():
  instructions = Instructions().try_instructions().exec(1)

  return instructions
</code></pre>

## Output Example

```solidity
{
    {
        "contract": "0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c"
        "contract_name": "ERC721"
        "sol_function":
            function _checkOnERC721Received(
                    address from,
                    address to,
                    uint256 tokenId,
                    bytes memory data
                ) private returns (bool) {
                    if (to.isContract()) {
                        try IERC721Receiver(to).onERC721Received(_msgSender(), from, tokenId, data) returns (bytes4 retval) {
                            return retval == IERC721Receiver.onERC721Received.selector;
                        } catch (bytes memory reason) {
                            if (reason.length == 0) {
                                revert("ERC721: transfer to non ERC721Receiver implementer");
                            } else {
                                /// @solidity memory-safe-assembly
                                assembly {
                                    revert(add(32, reason), mload(reason))
                                }
                            }
                        }
                    } else {
                        return true;
                    }
            }
    },
    {
        "sol_instruction":
            try IERC721Receiver(to).onERC721Received(_msgSender(), from, tokenId, data) returns (bytes4 retval) {
                            return retval == IERC721Receiver.onERC721Received.selector;
                        } catch (bytes memory reason) {
                            if (reason.length == 0) {
                                revert("ERC721: transfer to non ERC721Receiver implementer");
                            } else {
                                /// @solidity memory-safe-assembly
                                assembly {
                                    revert(add(32, reason), mload(reason))
                                }
                            }
            }
    }
}
```
