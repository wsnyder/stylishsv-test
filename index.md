# Defparams Deprecated

This is a style warning that the "defparam" statement is deprecated.  It is
recommended that designs instead use the '#(...)'  format to specify
parameters on an individual cell.

## Applicability/Adoption

It is recommended that all designs using Verilog 2001 and above follow this
guideline.

## Standards References

* IEEE 1364-2001 12.2 - New #() syntax introduced
* IEEE 1364-2005 12.2.1 - Recommending no defparams
* IEEE 1800-2005 25.2 - Deprecation of defparam
* IEEE 1800-2009 C.4.1 - Deprecation of defparam
* IEEE 1800-2012 C.4.1 - Deprecation of defparam
* IEEE 1800-2017 C.4.1 - Deprecation of defparam

## Example

#### Failing Example

````
module parameterized
   #(parameter int MY_PARAM = 0);
endmodule;

module upper;
  defparam p0.MY_PARAM = 1;  //<--- Warning
  parameterized p0();
endmodule
````

#### Repaired Example

````
module parameterized
   #(parameter int MY_PARAM = 0);
endmodule;

module upper;
  parameterized
     #(.MY_PARAM(1))  //<--- Repaired
     p0();
endmodule
````

## Supporting Tools

### SV Tests

| Test name | TODO |

### Veriable

| Warning name | forbid_defparam_rule |
| Example warning | TODO |
| Documentation Reference | TODO |

### Verilator

| Warning name | DEFPARAM |
| Example warning | `%Warning-DEFPARAM: ...: Suggest replace defparam assignment with Verilog 2001 #(.MY_PARAM(...etc...))` |
| Documentation Reference | [Verilator documentation for DEFPARAM](https://verilator.org/projects/verilator/wiki/Manual-verilator#DEFPARAM) |

### About this Page

This page is part of the [CHIPS Alliance TO-BE-NAMED-Sylish-System-Verilog project](https://chipsalliance.org/FIXME-url),
and under the open [CC BY-SA 4.0 license](https://creativecommons.org/licenses/by-sa/4.0).

<!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->

<!-- Note a theme like this might be good: https://idratherbewriting.com/documentation-theme-jekyll/index.html#build-the-theme -->
<!-- NOTE THIS TOO: http://www.cplusplus.com/reference/string/string/ -->

[![Sponsored by CHIPS Alliance!](https://wsnyder.github.io/stylishsv-test/badge-sponsor-chips-alliance.png)](https://chipsalliance.org)
