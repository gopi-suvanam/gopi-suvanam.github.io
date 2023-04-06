---
title: Option Pricing in JavaScript using Black-Scholes Formula
layout: post
description: Black-Scholes is a closed-form solution to option pricing and can easily be implemented in JavaScript for web-app development or experimetnation.
---

JavaScript can be used to implment Black-Scholes - a closed-form solution to option pricing.To price options using the Black-Scholes formula in JavaScript, you can follow these steps:

1. Define the necessary variables: You will need to define the current stock price, the strike price, the time until expiration (in years), the risk-free interest rate, and the stock's annualized volatility.

2. Calculate d1 and d2: These are the two parameters used in the Black-Scholes formula. d1 is calculated as [(ln(S/K) + (r + σ²/2)t)] / (σ√t), and d2 is calculated as d1 - σ√t.

3. Calculate the option price: The option price can be calculated using the Black-Scholes formula, which is:

4. Option price = S * N(d1) - K * e^(-rt) * N(d2)

Where S is the current stock price, K is the strike price, r is the risk-free interest rate, t is the time until expiration (in years), and N() is the cumulative normal distribution function.

Implement the cumulative normal distribution function: You can use a library like jStat or a custom implementation to calculate the cumulative normal distribution function. Alternatively, you can use an approximation like the one provided by the Abramowitz and Stegun handbook. Standard normal density function can be calculated as:

	ndist=function(z) {
	  return (1.0/(Math.sqrt(2*Math.PI)))*Math.exp(-0.5*z);
	}
	
Cumulative normal distribution does not have a closed form formula. But it can be approximated through:

	normalcdf=function(X){   //Approximation for cumulative standard normal distribution.
		var T=1/(1+.2316419*Math.abs(X));
		var D=.3989423*Math.exp(-X*X/2);
		var Prob=D*T*(.3193815+T*(-.3565638+T*(1.781478+T*(-1.821256+T*1.330274))));
		if (X>0) {
			Prob=1-Prob
		}
		return Prob
	}   
	
Black-Scholes price can be obtained using the code:

	black_scholes.call_price=function(S,K,r,v,t) { 
	  var sqt = Math.sqrt(t);
	  d1 = (Math.log(S/K) + r*t)/(v*sqt) + 0.5*(v*sqt);
	  d2 = d1 - (v*sqt);
	  delta = normalcdf(d1);
	  Nd2 = normalcdf(d2);
	  ert = Math.exp(-r*t);
	  nd1 = ndist(d1);
	  result={}
	  result['price']=S*delta-K*ert *Nd2;
	  result['gamma'] = nd1/(S*v*sqt);
	  result['vega'] = S*sqt*nd1;
	  result['theta'] = -(S*v*nd1)/(2*sqt) - r*K*ert*Nd2;
	  result['rho'] = K*t*ert*Nd2;
	  return (result );
	} //end of black_scholes call
	
The above code not only gives the price of the option but also gives "greeks" i.e. sensitivities of the prices to various factors. The above code is part of the library <a href="https://github.com/gopi-suvanam/di-libs/"> Di-Libs </a>. For experimenting use the notebook: [https://decentralized-intelligence.com/jsnb/#./examples/Black-Scholes.jsnb](https://decentralized-intelligence.com/jsnb/#./examples/Black-Scholes.jsnb).


