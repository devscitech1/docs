


uiGetNodePosition
=================

Get the position(s) of a node



Calling Sequence
~~~~~~~~~~~~~~~~


::

    position = uiGetNodePosition(tree, node)




Input parameters
~~~~~~~~~~~~~~~~

:tree Tree in which we look for position(s) of a node
: :node the node we look for position(s)
:



Output parameters
~~~~~~~~~~~~~~~~~

:position a matrix of string which contains node position(s).
:



Description
~~~~~~~~~~~

Get the position of a given node.



Examples
~~~~~~~~


::

    // We should create nodes(subTrees) before creating trees	
    leaf11 = `uiCreateNode`_('leaf 1.1', 'iconLeaf1.1', 'callbackLeaf1.1')
    leaf12 = `uiCreateNode`_('leaf 1.2', 'iconLeaf1.2', 'callbackLeaf1.2')
    leaf31 = `uiCreateNode`_('leaf 3.1', 'iconLeaf3.1', 'callbackLeaf3.1')
    leaf32 = `uiCreateNode`_('leaf 3.2', 'iconLeaf3.2', 'callbackLeaf3.2')
    node1 = `uiCreateNode`_('Node 1', 'iconNode1', 'callbackNode1')
    node2 = `uiCreateNode`_('Node 2', 'iconNode2', 'callbackNode2')
    node3 = `uiCreateNode`_('Node 3', 'iconNode3', 'callbackNode3')
    root = `uiCreateNode`_('Root', 'iconRoot', 'callbackRoot')
    
    treeNode1 = `uiCreateTree`_(node1, leaf11, leaf12)
    treeNode3 = `uiCreateTree`_(node3, leaf31, leaf32)
    treeRoot = `uiCreateTree`_(root, treeNode1, node2, treeNode3)
    
    // Get the position of node 'node1'
    position = uiGetNodePosition(treeRoot, node1)
    // will return 'position = ['1']'
    
    // Get the position of leaf 'leaf31'
    position = uiGetNodePosition(treeRoot, leaf31)
    // will return 'position = ['3.1']'




See Also
~~~~~~~~


+ `uiCreateNode`_ Creation of node (for Scilab Tree)
+ `uiCreateTree`_ Creation of a Tree
+ `uiDisplayTree`_ Printing a Tree in GUI mode
+ `uiDumpTree`_ Printing a Tree in the console (text mode)
+ `uiInsertNode`_ Insertion in a Tree
+ `uiDeleteNode`_ Deletion in a Tree
+ `uiConcatTree`_ Concatenation of Trees
+ `uiEqualsTree`_ Comparing two trees
+ `uiFindNode`_ Find node in Tree
+ `uiGetParentNode`_ Get Parent of a node
+ `uiGetChildrenNode`_ Get Children of a node


.. _uiInsertNode: uiInsertNode.html
.. _uiCreateNode: uiCreateNode.html
.. _uiDumpTree: uiDumpTree.html
.. _uiFindNode: uiFindNode.html
.. _uiDeleteNode: uiDeleteNode.html
.. _uiDisplayTree: uiDisplayTree.html
.. _uiCreateTree: uiCreateTree.html
.. _uiEqualsTree: uiEqualsTree.html
.. _uiGetParentNode: uiGetParentNode.html
.. _uiGetChildrenNode: uiGetChildrenNode.html
.. _uiConcatTree: uiConcatTree.html


