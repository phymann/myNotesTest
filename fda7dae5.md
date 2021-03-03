---
date: 2021-03-03T04:05
---

# Mathematica Tips

## Install packages

Find `$UserBaseDirectory/Applications` (typically at `~/.Mathematica/Applications`) and put the package (typically a `.m` file) there; then

```mathematica
<<NameOfPackage`
```

## Set up remote kernel connection

Steps to use remote kernel via local frontend:

### local part

- In `Kernel Configuration Options...` under `Evaluation` in menubar, add a new kernel and configure it by selecting `Local Machine`

- In `Arguments to MLOpen` of `Advanced Options`, type

```mathematica
-LinkMode Listen -LinkProtocol TCPIP
```

- In a notebook, choose `Notebook's Kernel` in `Evaluation` with this new one. Run

```mathematica
$Version
```

### remote part

Copy output of `$Version`, e.g., `51279@192.168.1.103,51280@192.168.1.103`,
run

```mathematica
$ParentLink = LinkConnect["51279@192.168.1.103,51280@192.168.1.103", LinkProtocol->"TCPIP"]
```

in `Wolframscript`
