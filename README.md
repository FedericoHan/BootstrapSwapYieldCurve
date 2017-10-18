# BootstrapSwapCurve
Get discount factors and zero rates from interest rate swaps'''implementation of "forward_substitution" from https://en.wikipedia.org/wiki/Bootstrapping_(finance)
Namely extracting discount_factors from market traded yield curve instruments, which are futures and deposits up to 1year,
and interest (IRS) or overnight indexed swaps (OIS).

Key concept on a fixed IRS, fair value is 0 at start, via no-arbitrage argument, assuming a notional of $1 

1year_IRS:  disc_factor1* ($1 + coup_1) = $1   
2year_IRS:  disc_factor1 * coup_2 + disc_factor2*($1 + coup_2) = $1
3year_IRS:  disc_factor1 * coup_3 + disc_factor2 * coup3 + disc_factor3 * ($1 + coup_3) = $1


Variation of Chapter5 from James WeiMing "Mastering Python For Finance"   '''

