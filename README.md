# BootstrapSwapCurve: derive discount factors (and zero rates) from interest rates swaps

Part 1 of 2 uses Bloomberg API with TIA wrapper to download USD Interest Rate Swaps (IRS) up to 30 years. I've taken yearly coupons, Act/360 instead of semi-annual 30/360, for simplicity.  
If you do not have access to Bloomberg, can just type manually or try a different API (quandl?) to get the market yields.  

Part 2 of 2 creates a class object, wherein the data from Part 1 is loaded 
unto a Python dictionary, and then discount factors (ie equivalent to zero-coupon bonds) and zero-rates are bootstrapped.  

In essence, it's the ''implementation of "forward_substitution" from https://en.wikipedia.org/wiki/Bootstrapping_(finance)

Ie. extracts discount_factors from market traded yield curve instruments, which are futures and deposits up to 1year,
and interest (IRS) swaps from 1y to 30yrs (could as easily use overnight indexed swaps (OIS).)  

Key concept on a fixed IRS, fair value is 0 at start, via no-arbitrage argument, assuming a notional of $1 (analogously, an IRS is the equivalent of an unfunded bond position, with it's 'price' being 'par').

1year_IRS:  disc_factor1* ($1 + coup_1) = $1   
2year_IRS:  disc_factor1 * coup_2 + disc_factor2*($1 + coup_2) = $1
3year_IRS:  disc_factor1 * coup_3 + disc_factor2 * coup3 + disc_factor3 * ($1 + coup_3) = $1
..an so forth.


Variation of Chapter5 from James WeiMing "Mastering Python For Finance" .

This is a synopsys of what is done by various pricers (minus of course a more proper daycount calendar but even without it, we get less than 2bps away on 30yrs, from BBG data) and, these days, collateral adjustments perhaps.  '''

