# FX Asset sHedge

The FX assets hedge model is employed to conduct the hedge effectiveness test for the foreign currency denominated floating rate LIBOR assets using CAD funding. The hedging derivative is a cross currency interest rate swap or accumulator swap (https://finpricing.com/lib/FxAccumulator.html). The hedging is designated as the Cash Flow Hedging in which both interest rate risk and foreign exchange risk are hedged. 

A hypothetical cross currency interest rate swap (XCIRS), with the floating leg terms matching the critical terms of the hedged FC floating rate assets, is used as the proxy measure. The actual hedging derivative is another XCIRS. Specifically, the trade, upon which the model is intended to target, is substituted by a cross currency swap, which is hedged by another XCIRS.

The test involves the computation of present value and the generation of projected future values of cash flows for certain number of random scenarios.

The first step is to get the random scenarios for all four legs involved in the two cross currency swaps by plugging all the transaction details (i.e. notional principal, effective date, maturity date, cash flow frequency, type of interest paid, currency, swap structure) into the model. We need to run the model four times. The model has been altered so that the four cash flows can be generated for each scenario. It is important to record each generated scenario and synchronize each run.

For example, if the random rate is based on 30 September 2004, we shall calculate the rate change between the spot rates on 31 December 2004 and 30 September 2004. This rate change is then applied to the current month-end spot rate. The values of the hypothetical derivative and the hedging derivative are converted into one currency using exchange rates associated with each scenario.

Note that the method of generating foreign exchange rate shock adopted here is same as that for the interest rate in the model.  The correlation between the interest rates and the foreign exchange rate are imbedded in the scenario, since exactly the same historical date is used in each scenario. Note that, unlike the usual cash flow hedging in which the fixed leg of swap is not considered, all the values of the four legs are taken into account so that the foreign exchange risk is fully captured.

Once we determine the present value and all the projected future values of the scenarios for the hypothetical derivative and the hedging derivative, we could conduct effectiveness tests, which includes Prospective Test and Retrospective Test. Both the test measures and corresponding passing criterion are the same as those implemented in the current model.

The Ineffectiveness Test is also implemented, which is calculated by comparing the cumulative change in fair values of the hypothetical derivative and the cumulative change in fair value of the actual hedging derivative. The values for calculating ineffectiveness test are obtained from Infinity. The rationale is there are more forward points in Infinity compared to that in the model to make the results more accurate.




