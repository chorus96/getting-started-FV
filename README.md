# Getting started with Formal Verification

## Formally Verify a simple Verilog example

Take a look at the example: [counter.v](counter.v). We have one formal property, an assertion that the counter will always be less than `MAX_AMOUNT`.
[counter.sby](counter.sby) is the [configuration file](https://symbiyosys.readthedocs.io/en/latest/reference.html).

Run this command to Formally Verify the counter example:

    sby -f counter.sby

The `-f` switch removes previous test results. You will see some log output from the tool and the last line shows the result: FAIL.
When the tools find a way to break an assertion they generate a trace file. 

* If the test failed bounded model checking (BMC), the trace will be written to counter/engine_0/trace.vcd. 
* If the test failed induction, the trace will be written to counter/engine_0/trace_induct.vcd.

The BMC failed because the solver was able to set the initial value of the count register to a value greater than `MAX_AMOUNT`. 
Fix this by setting a default value for the register and then run the verification again. 

To learn more about Formal Verification, see the [resources section below](#Resources)

# Resources

* Symbiyosys docs https://symbiyosys.readthedocs.io/en/latest/
* Some examples to try: https://github.com/YosysHQ/SymbiYosys/tree/master/docs/examples
* Videos and Presentations on Formal Verification: https://www.youtube.com/c/SymbioticEDA
* Dan Gisslequist's blog contains a lot of posts about FV: http://zipcpu.com/
* You can also request a demo or book a training course by contacting us at https://www.symbioticeda.com/
