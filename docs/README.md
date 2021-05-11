fluent-iterable - v0.1.0

# fluent-iterable - v0.1.0

## Table of contents

### Type aliases

- [FilterList](README.md#filterlist)
- [OrderField](README.md#orderfield)
- [OrderType](README.md#ordertype)

### Functions

- [and](README.md#and)
- [between](README.md#between)
- [by](README.md#by)
- [byExpr](README.md#byexpr)
- [equals](README.md#equals)
- [group](README.md#group)
- [gte](README.md#gte)
- [isIn](README.md#isin)
- [lastHit](README.md#lasthit)
- [lte](README.md#lte)
- [min](README.md#min)
- [or](README.md#or)
- [orderBy](README.md#orderby)
- [select](README.md#select)
- [topHit](README.md#tophit)
- [where](README.md#where)

## Type aliases

### FilterList

Ƭ **FilterList**: (*object* \| *undefined*)[]

___

### OrderField

Ƭ **OrderField**: [*string*, [*OrderType*](README.md#ordertype)]

___

### OrderType

Ƭ **OrderType**: ``"asc"`` \| ``"desc"``

## Functions

### and

▸ **and**<T\>(`items`: T): *undefined* \| *object*

Returns an and filter (bool.must)

#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | (*undefined* \| *object*)[] |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `items` | T | the list of conditions |

**Returns:** *undefined* \| *object*

The and filter

___

### between

▸ **between**<T, V\>(`field`: T, `from`: V \| *undefined*, `to`: V \| *undefined*): *undefined* \| { `range`: {}  }

Returns a range filter with gte and lte

#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | *string* |
| `V` | - |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `field` | T | The field to be compared |
| `from` | V \| *undefined* | the lower value |
| `to` | V \| *undefined* | the upper value |

**Returns:** *undefined* \| { `range`: {}  }

The between filter

___

### by

▸ **by**<T, Order, Size, AggName, Agg\>(`field`: T, `order`: Order, `size`: Size, `aggregate`: Agg): *Record*<string, object\>

Returns a grouping by term

#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | *string* |
| `Order` | [*OrderType*](README.md#ordertype) \| [*OrderField*](README.md#orderfield) |
| `Size` | *number* |
| `AggName` | *string* |
| `Agg` | { [aggName in string]: object} |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `field` | T | The field to be grouped |
| `order` | Order | The order to be applied. Can be a return of *orderBy* function, or simply a "asc" or "desc", if you want to order by the grouping term |
| `size` | Size | How many items must be returned |
| `aggregate` | Agg | the inner aggregation to be made. This is where you specify the fields to be returned somehow |

**Returns:** *Record*<string, object\>

the aggregate by painless script object;

___

### byExpr

▸ **byExpr**<T, Order, Size, AggName, Agg\>(`field`: T, `order`: Order, `size`: Size, `aggregate`: Agg): *Record*<string, object\>

Returns a grouping by painless script expression

#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | [*string*, *string*] |
| `Order` | [*string*, [*OrderType*](README.md#ordertype)] |
| `Size` | *number* |
| `AggName` | *string* |
| `Agg` | { [aggName in string]: object} |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `field` | T | A Tuple where the fist element is the grouping name, and the second the grouping expression |
| `order` | Order | The order to be applied. Can be a return of *orderBy* function |
| `size` | Size | How many items must be returned |
| `aggregate` | Agg | the inner aggregation to be made. This is where you specify the fields to be returned somehow |

**Returns:** *Record*<string, object\>

the aggregate by painless script object;

___

### equals

▸ **equals**<T, V\>(`field`: T, `value`: V \| *undefined*): *undefined* \| { `terms`: {}  }

Returns a filter of equals comparison

#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | *string* |
| `V` | - |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `field` | T | The field to be compared |
| `value` | V \| *undefined* | the value to be compared |

**Returns:** *undefined* \| { `terms`: {}  }

The equality filter

___

### group

▸ **group**<By\>(`aggs`: By): *object*

Envelops a grouping query, with 0 results for non grouped items

#### Type parameters

| Name | Type |
| :------ | :------ |
| `By` | *Record*<string, object\> |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `aggs` | By | The aggregation to be enveloped. Must be a return of *By* function |

**Returns:** *object*

| Name | Type |
| :------ | :------ |
| `aggs` | By |
| `size` | *number* |

An enveloped grouping object

___

### gte

▸ **gte**<T, V\>(`field`: T, `value`: V): *undefined* \| { `range`: {}  }

Returns a range filter with gte

#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | *string* |
| `V` | - |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `field` | T | The field to be compared |
| `value` | V | the lower value |

**Returns:** *undefined* \| { `range`: {}  }

The gte filter

___

### isIn

▸ **isIn**<T, V\>(`field`: T, `values`: V[] \| *undefined*): *undefined* \| { `terms`: {}  }

Returns a filter of "in" comparison

#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | *string* |
| `V` | - |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `field` | T | The field to be compared |
| `values` | V[] \| *undefined* | The list of accepted values |

**Returns:** *undefined* \| { `terms`: {}  }

The in filter

___

### lastHit

▸ **lastHit**<T, Order, Fields\>(`sort`: Order, `fields?`: Fields): *object*

Returns a tpp hit aggregate expression of size 1

#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | *string* |
| `Order` | { [field in string]: OrderType}[] |
| `Fields` | *string*[] |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `sort` | Order | The order to be applied. Must be a return of *orderBy* function |
| `fields?` | Fields | the fields to be returned. If not informed, all fields are returned |

**Returns:** *object*

| Name | Type |
| :------ | :------ |
| `tops` | *object* |
| `tops.top_hits` | *object* |
| `tops.top_hits._source` | *undefined* \| { `includes`: Fields  } |
| `tops.top_hits.size` | *number* |
| `tops.top_hits.sort` | Order |

the top hit aggregate object of size 1

___

### lte

▸ **lte**<T, V\>(`field`: T, `value`: V \| *undefined*): *undefined* \| { `range`: {}  }

Returns a range filter with lte

#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | *string* |
| `V` | - |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `field` | T | The field to be compared |
| `value` | V \| *undefined* | the upper value |

**Returns:** *undefined* \| { `range`: {}  }

The lte filter

___

### min

▸ **min**<T\>(`field`: T, `alias`: *string*): *object*

Returns a min aggregate expression

#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | *string* |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `field` | T | the field in question |
| `alias` | *string* | the name for the aggregation |

**Returns:** *object*

the min aggregation

___

### or

▸ **or**<T\>(`items`: T): *undefined* \| *object*

Returns an or filter (bool.should)

#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | (*undefined* \| *object*)[] |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `items` | T | the list of conditions |

**Returns:** *undefined* \| *object*

The or filter

___

### orderBy

▸ **orderBy**<Fields, Orders\>(`orders`: Orders): { [t in string]: OrderType}[]

Format a ordering object

#### Type parameters

| Name | Type |
| :------ | :------ |
| `Fields` | *string* |
| `Orders` | [Fields, [*OrderType*](README.md#ordertype)][] |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `orders` | Orders | the sequence of tuples of field and asc/desc, to defined the ordering |

**Returns:** { [t in string]: OrderType}[]

the ordering object

___

### select

▸ **select**<Fields\>(`includes`: Fields \| *undefined*): *undefined* \| { `includes`: Fields  }

Envelops a list of fields to be chosen

#### Type parameters

| Name | Type |
| :------ | :------ |
| `Fields` | *string*[] |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `includes` | Fields \| *undefined* | The fields to be chosen |

**Returns:** *undefined* \| { `includes`: Fields  }

The enveloped object

___

### topHit

▸ **topHit**<T, Order, Fields\>(`size`: *number*, `sort`: Order, `fields?`: Fields): *object*

Returns a tpp hit aggregate expression

#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | *string* |
| `Order` | { [field in string]: OrderType}[] |
| `Fields` | *string*[] |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `size` | *number* | the number of items to be returned |
| `sort` | Order | The order to be applied. Must be a return of *orderBy* function |
| `fields?` | Fields | the fields to be returned. If not informed, all fields are returned |

**Returns:** *object*

| Name | Type |
| :------ | :------ |
| `tops` | *object* |
| `tops.top_hits` | *object* |
| `tops.top_hits._source` | *undefined* \| { `includes`: Fields  } |
| `tops.top_hits.size` | *number* |
| `tops.top_hits.sort` | Order |

the top hit aggregate object

___

### where

▸ **where**<Query\>(`query`: Query \| *undefined*): { `query`: Query  } \| { `query`: *undefined*  }

Envelops filter/query conditions

#### Type parameters

| Name | Type |
| :------ | :------ |
| `Query` | *undefined* \| *object* |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `query` | Query \| *undefined* | the query to be enveloped |

**Returns:** { `query`: Query  } \| { `query`: *undefined*  }

the enveloped query or an empty object, when query is undefined