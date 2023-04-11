web3-async-attempts
===================

A set of completely unfactored (i.e., flat, nearly-offensive, ugly) Python scripts that demonstrate a variety of attempts to utilize either asynchronous or parallel processing with Web3.py .

This is a current successful demonstration of asynchronous web3.py contract calls and an archived, reduced-set of historical attempts.

General Flow -- UPDATE (2023/04/11)
=============
All scripts try to perform the same basic work:
1. Perform a GraphQL query to obtain a subset of Uniswap V3 liquidity pools;
2. Use Web3.py AsyncHTTP provider to make contract calls for slot0 data of liquidity pools;
3. Use Web3.py AsyncHTTP provider to make contract calls for tick bitmap data of liquidity pools; and
4. Process the results somehow (typically just printing the final results out).

Scripts that failed to parallelize the contract calls have been placed in the `archived_attempts` directory. Until recently, web3.py's asynchronous HTTP provider did not allow for contract call operations, so we had to use the regular HTTP provider with these attempts.

Current successful version uses both `AsyncWeb3` and `AsyncHTTPProvider` classes and refactored `Web3.toCheckSumAddress` to `Web3.to_checksum_address` (i.e., it has become more "Pythonic" in the Web3.py library itself).

Archived Scripts Descriptions
====================
* _web3-iteration.py_ is the most basic approach, kind of a control to measure (completely unscientifically) the other script performance against.
* _web3_parallelized.py_ is probably the most effective way to make many HTTP provider based calls against the blockchain since it utilizes concurrent.futures, which allows for true parallel processing, not just asynchronous processing.
* _web3_futures.py_ utilizes an asyncio futures approach to try and perform asynchronous processing of these requests.
* _web3_create_futures.py_ is like web3_futures.py, but uses a slightly different approach.
* _web3_async_gather.py_ uses the standard gather approach for asyncio, to generate tasks that are supposedly run asynchronously.

--> You need to replace the value of W3_HTTP_PROVIDER with whatever Web3 HTTP provider endpoint URL (or its environmental variable) you plan to use.  