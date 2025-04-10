# ICE 6: Time Division Multiplexing

VHDL for ECE 281 [ICE 6](https://usafa-ece.github.io/ece281-book/ICE/ICE6.html)

Targeted toward Digilent Basys3. Vivado 2024.2

Tested on Windows 11.

---

## Build the project

You can simply open `tdm.xpr` and Vivado will do the rest!

## GitHub Actions Testbench

The workflow uses the [setup-ghdl-ci](https://github.com/ghdl/setup-ghdl-ci) GitHub action
to run a *nightly* build of [GHDL](https://ghdl.github.io/ghdl/).

The workflow uses GHDL to analyze, elaborate, and run the entity specified in the `.github/workflows/testbench.yml`.

```yaml
env:
  TESTBENCH_ENTITY: TDM4
```

If successful then GHDL will quietly exit with a `0` code.
If any of the `assert` statements fail **with** `severity failure` then GHDL will cease the simulation and exit with non-zero code; this will also cause the workflow to fail.
Assert statements of other severity levels, such as "error" w


Documentation: I asked Duke why I was getting a red underline for 
	port map ( 
       i_clk   => w_clk,
       i_reset => w_reset,
       i_D3    => w_D3,
       i_D2    => w_D2,
       i_D1    => w_D1,
       i_D0    => w_D0,
       o_data  => f_data,
       o_sel   => f_sel_n
and he said it was because I was using ; instead of , . C2C Duessler told me I needed to add a clk = ‘0’ so I did because before I only had it ‘1’. I checked my answers with C3C Randolph, and he told me that I needed to check the discussion chat in 281 teams page to see how to convert my waveform into binary. He also told me that for question 2, inputs dont actually determine how wide the data vectors are, bc thats my kwidth. also, they dint determine which signals are multiplexed; they ARE the signals being multiplexed. when the system is instantiated, they are mapped then too (as in when TDM4 is created they are mapped to that). He also told me that I D3 was wrong, so I relooked and saw D1 was correct.
