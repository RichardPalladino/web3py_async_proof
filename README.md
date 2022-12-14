web3-async-attempts
===================

A set of completely unfactored (i.e., flat, nearly-offensive, ugly) Python scripts that demonstrate a variety of attempts to utilize either asynchronous or parallel processing with Web3.py .

This is a reduced set of all the attempts.

General Flow
=============
All scripts try to perform the same basic work:
1. Perform a GraphQL query to obtain a subset of Uniswap V3 liquidity pools;
2. Use Web3.py HTTP provider to make contract calls for slot0 data of liquidity pools;
3. Use Web3.py HTTP provider to make contract calls for tick bitmap data of liquidity pools; and
4. Process the results somehow (typically just printing the final results out).

Note: Web3.py's asynchronous HTTP provider does not allow for contract call operations, so we had to utilize the regular HTTP provider with these attempts.

Script descriptions
====================
* _web3-iteration.py_ is the most basic approach, kind of a control to measure (completely unscientifically) the other script performance against.
* _web3_parallelized.py_ is probably the most effective way to make many HTTP provider based calls against the blockchain since it utilizes concurrent.futures, which allows for true parallel processing, not just asynchronous processing.
* 

--> You need to replace the value of W3_HTTP_PROVIDER with whatever Web3 HTTP provider endpoint URL (or its environmental variable) you plan to use.  