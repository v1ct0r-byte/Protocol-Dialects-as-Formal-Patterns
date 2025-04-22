# A Composable Theory of Lingos for Protocol Dialects

## Protocols under consideration

Since dialects are generalized protocol transformation we need some concrete specifications of protocols to work with. We selected the [Needham–Schroeder Public-Key Protocol (NSPK)](https://en.wikipedia.org/wiki/Needham%E2%80%93Schroeder_protocol) and [MQTT](https://en.wikipedia.org/wiki/MQTT). We have a Maude specification for each of them inside folder `protocols`. These Maude specifications are generalized and abstract models of the protocol's formal semantics.

## Lingos

We have a collection of parameterized lingos, each with a series of parameteric modules that make them generic in various ways. The first three are general enough to work over many trivial data-types. The last one can only work over natural numbers, but we allow the specification of the size of those numbers.

- Identity (`/protocols/identity-lingo.maude`)
- Split (`/protocols/split-lingo.maude`)
- XOR (`/protocols/xor-lingo.maude`)
- D&C (`/protocols/d&c-lingo.maude`)

## Running examples

All executable examples are inside folder `running-examples`. Each of the files inside is a concrete example of applying the notion of dialects to a protocol with some lingo/s. Now we will list all executable examples with a brief description of the environment they represent.
 
The following are sets of executable runnning examples. We have grouped them by type of scenario. We add to each of them a small explanation of what they execute.

### Dialects with a "simple" lingo

- **sin-id-mqtt:** Dialect with the IDENTITY lingo. Base protocol is MQTT.
- **sin-d&c-mqtt:** Dialect with divide and check (D&C) lingo. Base protocol is MQTT.
- **sin-xor-mqtt:** Dialect with the XOR lingo. Base protocol is MQTT.
- **sin-xor-nspk:** Dialect with the XOR lingo. Base protocol is NSPK.
- **sin-edxor-mqtt:** Dialect with the error-detecting XOR lingo. Base protocol is MQTT.
- **sin-transxor-mqtt:** Dialect with the error-detecting XOR resulting from transforming the XOR lingo. Base protocol is MQTT.
- **sin-split-nspk:** Dialect with SPLIT lingo. Base protocol is NSPK.
- **sin-xor2K-mqtt:** Example of Dialect that uses the XOR lingo with the same key two times before updating the parameter. Base protocol is MQTT.
- **sin-laxor-mqtt:** Dialect with a left-adapted xor lingo that works on Natural numbers. The base protocol is MQTT with Strings. The adapter extends the lingo so it can work over Strings by converting them to natural numbers and back to Strings.
- **sin-xorNat-mqtt:** Dialect with a lingo based on the built in XOR operation on Natural numbers. Base protocol is MQTT.

### Hotizontal composition

- **sin-dilingo-mqtt-biased:** Horizontal composition of two XOR lingos (XOR with XOR'), using a biased dice, over MQTT.
- **sin-dilingo-mqtt-fair:** Horizontal composition of two XOR lingos (XOR with XOR'), using a fair dice, over MQTT.
- **sin-dilingo'-mqtt-biased:** Horizontal composition of XOR and D&C lingos, using a biased dice, over MQTT.
- **sin-trilingo-nspk-fair:** Horizontal composition of XOR, D&C and SPLIT, using a fair dice, over NSPK.

### Fucntional composition

- **sin-xor&split-nspk:** Dialect with a lingo that is the functional composition of XOR and SPLIT. Base protocol is NSPK.
- **sin-xor&dc-mqtt:** Dialect with a lingo that is the functional composition of XOR and D&C. Base protocol is MQTT.
- **sin-xor&dc&split-mqtt:** Dialect with a lingo that is the functional composition of XOR, D&C and SPLIT. Base protocol is MQTT.

# Replication of experiments

In order to replicate the experiments one has to follow these steps:

1. Have **Maude 3.5** installed. This can be done following the instructions in the [Maude download and installation](https://maude.cs.illinois.edu/w/index.php/Maude_download_and_installation) web page.
2. Download the zip file in your machine.
3. Open a terminal on the parent folder containing the downloaded files.
4. Launch Maude (we recommend using flag `--no-advise` for a cleaner output).
5. Load any of the files, listed in section **Running examples** above, that are inside the `running-examples` folder of the repository. These files contain at the end a `fair rewrite` command that will exectue an instance of the dialect infraestructure. This command will return a final state of the execution of that protocol. For more information in the semantics of each protocol, please see its Maude specification.
6. If one wants to execute any other commands like `search`, we recommend writting them at the end of the running examples files.
