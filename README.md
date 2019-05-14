# DTH Development

## General workflow

[Flowchart here](dev_flowchart.svg)

## Style guidelines

```
/**
 * copyright SmartThings 20XX here
 *
 */

import package.name.here

...

if (no_space_after_if) {
    assert_fail()
} else if (conditional_is_very_long && 
            it_should_have_its_own_line ||
            you.told_to_fix_it()) {
    some_code.goes_here()
} else if (empty_block) {} #just put it on one line

...

def camelCaseFunctions(descriptive_argument_name) {
    # if you're doing something device-specific or hacky, leave a comment
    device.getDataValue("manufacturer") == "Yale" ? do_this() : []
}

def getTHIS_IS_A_CONSTANT {0xDEADBEEF}
```

- copyright statement first
- imports under copyright statement
- tabs, not spaces
- "K&R style" braces:
    - opening braces on same line as statement
    - closing braces on their own line except for `else-ifs`
- one empty line between functions
- space after `if` before conditions
- break up huge `if` conditionals after the operator, one tab beyond where top conditional starts
    - same applies to long function calls & explicit lists
- function names are `camelCased`
- constants are in `CAPS_WTIH_UNDERSCORES`

## How to write a DTH

Mostly-complete guide [here](https://smartthings.atlassian.net/wiki/spaces/~819110175/pages/482607274/Hub-Connected+Device+Z-Wave+Zigbee+DTH+Development+Guidelines).

### UI-Metadata Guide

Donald actively maintains [this guide](https://smartthings.atlassian.net/wiki/spaces/UM/pages/529716072/UI+Metadata+Generator+Interface).

### New style of ZigBee fingerprints

Just include `manufacturer` and `model`. No more need for `inClusters`, `outClusters`, or `profileId`.

## Development Risks

- changes to existing DTHs
- (re)moving fingerprints
- `device.getDataValue` dependencies
- device-specific configurations
- changing capabilities
- local execution restrictions/bugs

## Post-publishing bugs

If you wrote it, you support it.