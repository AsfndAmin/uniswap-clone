# uniswap-clone

first deploy factory contract of uniswap v2 by adding
bytes32 public constant INIT_CODE_PAIR_HASH = keccak256(abi.encodePacked(type(UniswapV2Pair).creationCode));
in uniswapV2Factory contract and deploy and get this hash from there
now go to library UniswapV2Library and paste this hash in the
    function pairFor(address factory, address tokenA, address tokenB) internal pure returns (address pair) {
        (address token0, address token1) = sortTokens(tokenA, tokenB);
        pair = address(uint(keccak256(abi.encodePacked(
                hex'ff',
                factory,
                keccak256(abi.encodePacked(token0, token1)),
                hex'02c6f4b788e6e8dea4b2efda29c1e2c181e989d6df4fd86d40b0b9a92dbad4f4' // init code hash
            ))));
    }
    in hex location and remove 0x from start.
    now deploy the router contract.
    create pair
    addliquidity give allowance of both tokenA and tokenB to the router contract.
    To remove liquidity you have to give the allowance to the router for the lp tokens get the lp token contract address and compile erc20 contract from test file and give allowance to the router contract to remove liquidity.
