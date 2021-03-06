
# Data Types
NPL Language has the following base data types
 - bit & bit-array
 - varbit 
 - list
 - const
 - enum & auto_enum
 - struct & stuct-array

# Parser Construct
The Parser constructs define:
 - Header, consists of an ordered set of fields with fixed or variable lengths
 - Header group, consists of different header 
 - Packets, consists of header groups
 - Connectivity among the header types, to form the parse tree

Header is defined using struct data type. Header fields are defined using bit and bit-array.

Two additional options are available:
 - varbit - to specify a variable length field.
 - header_length_exp - to specify header length in case of varbit usage. 


### Data Types & Parser Example 

We have created an example to illustrate Data Types supported in NPL and Parser construct which does

1. Define packet header using NPL supported data-types.
2. Define parsing logic.
3. Parse incoming packet.
4. Extract packet contents to header fields.
5. Checks if particular header is present in incoming packet and prints its value which you will see in ``` BMODEL ``` xterm window.

To execute this example, follow below steps

1. Make sure [build environment](https://github.com/nplang/NPL-Tutorials#npl-build-enivronment) was properly setup as described earlier
2. Once the environmental variables were setup execute below commands. 
````

export NPL_EXAMPLES=/home/npl/ncsc-1.3.3rc4/examples/npl_tidbits/constructs
cd $NPL_EXAMPLES/data_types_and_parser 
make fe_nplsim
make nplsim_comp
make nplsim_run

````

Now you will see two xterm windows one with name ```BMODEL``` and another with ```BMCLI```. You can now inject packet using below command  from original console widow where you compiled the NPL code. 

````
python bm_tests/corp_net/testPkt.py

````

The above testPkt.py sends the following packets to port-0 of the Behavioral Model
````

Once you build and run of Data Types and Constructs, send the following packets to port-0 of BMODEL:
Double-tagged packet [OUTER:TPID(0x88A8),VLAN-10], [INNER: TPID(0x8100), VLAN-20].
Single-outer-tagged packet [OUTER:TPID(0x88A8),VLAN-10].
Single-inner-tagged packet [INNER:TPID(0x8100),VLAN-20].
Untagged packet.
IP packet with options.

````

On the BMODEL window you will see prints that display parsed packets from NPL program. 

You can experience complete NPL program for this example which was located at below location

````

$NPL_EXAMPLES/data_types_and_parser/npl/data_types_and_parser.npl

````

## Next Tutorial 

Congratulations :+1:

You have experienced how to use ``` Data Types & Parser ``` construct in NPL Language. You can now move on to next example [Function Construct](https://github.com/nplang/NPL-Tutorials/tree/master/NPL-Tidbits/Function)
