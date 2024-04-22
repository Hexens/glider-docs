# IfInstruction.first\_false\_instruction()

`first_false_instruction() →` [`Instruction`](../)

The function returns the first instruction for the false-case scenario of the if-statement

## Example

for the function:

```solidity
function write(buffer memory buf,uint off,bytes memory data,uint len) internal pure returns(buffer memory) {
    //...
    assembly {
      //...
      
      if gt(add(len,off),buflen) {
        mstore(bufptr,add(len,off))
      }
      src := add(data,32)
    }
   //...
  }
```

The query (exec numbers are tuned here to match that exact if-statement)

<pre class="language-python"><code class="lang-python"><strong>from glider import *
</strong>
def query():
  instructionlist = Instructions().if_instructions().exec(1,100)
  
  first_false = instructionlist[0].first_false_instruction()

  return first_false.next_instruction()
</code></pre>

## Output

```solidity
"root":{4 items
"contract":string"0xf3DC505d1B0530493Ea5fcfc86f2C9c65975006B"
"contract_name":string"BufferChainlink"
"sol_function":solidity
function write(buffer memory buf,uint off,bytes memory data,uint len) internal pure returns(buffer memory) {
    require(len <= data.length);
 
    if (off + len > buf.capacity) {
      resize(buf,max(buf.capacity,len + off) * 2);
    }
 
    uint dest;
    uint src;
    assembly {
      
      let bufptr := mload(buf)
      
      let buflen := mload(bufptr)
      
      dest := add(add(bufptr,32),off)
      
      if gt(add(len,off),buflen) {
        mstore(bufptr,add(len,off))
      }
      src := add(data,32)
    }
 
    
    for (; len >= 32; len -= 32) {
      assembly {
        mstore(dest,mload(src))
      }
      dest += 32;
      src += 32;
    }
 
    
    uint mask = 256 ** (32 - len) - 1;
    assembly {
      let srcpart := and(mload(src),not(mask))
      let destpart := and(mload(dest),mask)
      mstore(dest,or(destpart,srcpart))
    }
 
    return buf;
  }
"sol_instruction":solidity
src := add(data,32)
}
```



As can be seen, the if-statements inside assembly blocks are also handled by the function

