# BootstrapSwapCurve
Part 1 of 2 uses Bloomberg API with TIA wrapper to download USD Interest Rate Swaps (IRS) up to 30 years.

Part 2 of 2 feeds creates a class object, wherein the data from above (it can be fed manually of course) is loaded 
unto a Python dictionary, and then discount factors (ie zero coupon bond equivalents) and zero-rates are bootstrapped.  

In essense, it's ''implementation of "forward_substitution" from https://en.wikipedia.org/wiki/Bootstrapping_(finance)

Ie. extracts discount_factors from market traded yield curve instruments, which are futures and deposits up to 1year,
and interest (IRS) (could as easily use overnight indexed swaps (OIS).)

Key concept on a fixed IRS, fair value is 0 at start, via no-arbitrage argument, assuming a notional of $1 

1year_IRS:  disc_factor1* ($1 + coup_1) = $1   
2year_IRS:  disc_factor1 * coup_2 + disc_factor2*($1 + coup_2) = $1
3year_IRS:  disc_factor1 * coup_3 + disc_factor2 * coup3 + disc_factor3 * ($1 + coup_3) = $1
..an so forth.


Variation of Chapter5 from James WeiMing "Mastering Python For Finance"   '''

