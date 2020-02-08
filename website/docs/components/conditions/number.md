---
title: number
type: condition
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/condition/number.go
-->


Checks the contents of a message parsed as a 64-bit floating point number
against a logical [operator](#operators) and an argument.


import Tabs from '@theme/Tabs';

<Tabs defaultValue="common" values={[
  { label: 'Common', value: 'common', },
  { label: 'Advanced', value: 'advanced', },
]}>

import TabItem from '@theme/TabItem';

<TabItem value="common">

```yaml
number:
  operator: equals
  arg: 0
```

</TabItem>
<TabItem value="advanced">

```yaml
number:
  operator: equals
  arg: 0
  part: 0
```

</TabItem>
</Tabs>

This condition is useful when paired with the [`check_field`](/docs/components/conditions/check_field) and
[`check_interpolation`](/docs/components/conditions/check_interpolation) conditions to check a
number condition against arbitrary metadata or fields of messages.

## Fields

### `operator`

`string` An [operator](#operators) to apply.

### `arg`

`number` An argument to check against. For some operators this field not be required.

### `part`

`number` The index of a message within a batch to test the condition against. This
field is only applicable when batching messages
[at the input level](/docs/configuration/batching).

Indexes can be negative, and if so the part will be selected from the end
counting backwards starting from -1.

## Operators

### `equals`

Checks whether the value equals the argument.

### `greater_than`

Checks whether the value is greater than the argument. Returns false if the
value cannot be parsed as a number.

### `less_than`

Checks whether the value is less than the argument. Returns false if the value
cannot be parsed as a number.

## Examples

You can test a number condition against the size of a message batch with:

``` yaml
check_interpolation:
  value: ${!batch_size}
  condition:
    number:
      operator: greater_than
      arg: 1
```
