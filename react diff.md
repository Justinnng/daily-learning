react diff

1.只会对相同层级的节点进行比较； 2.只有删除、创建操作，没有移动操作； 3.由于没做性能优化，所以官方建议少做这样的跨层级操作；

1.如果是同一个类的组件，则会继续往下diff运算； 2.如果不是一个类的组件，那么直接删除旧的，创建新的；

diff的时候，总是比较同一层级的节点们，这是前提，接下来提供了三种节点的操作：
插入：INSERT_MARKUP
删除：REMOVE_NODE
移动：MOVE_EXISTING
注意：每个节点都有在他们的层级唯一的key作为标识。


DOM节点跨层级的操作不做优化，因为很少这么做，这是针对的tree层级的策略；
对于同一个类的组件，会生成相似的树形结构，对于不同类的组件，生成不同的树形结构，这是针对conponent层级的策略；
对于同一级的子节点，拥有同层唯一的key值，来做删除、插入、移动的操作，这是针对element层级的策略；
