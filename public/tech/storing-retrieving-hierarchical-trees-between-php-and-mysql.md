PHP, Mysql and hierarchical trees
=================================

### Statement ###

*Hierarchical structures in mySQL & PHP needs preperation*

### Scenario ###

Its easy to create relations in mySQL by connecting columns.
However, once you are in PHP, its not really easy to convert this into an associative array.
Because when you select all needed records from the database, you get a plain list of all nodes.

### How to convert records to nodes ###

Basically, you need to know which is who's parent, and at what position(weight) the node should be positioned.

### Example ###

Suppose your sql table layout is :

    +------------------+
    | id(int11)        |
    | parent_id(int11) |
    | weight(int11)    | <- amazing ascii-art
    | title_menu(text) |    
    | content(text)    |
    +------------------+

### PHP Code ###

    $treeManager     = treeManager::get();
    $records         = $db->getArrayFromSql( "SELECT * FROM mytable" );
    // here we have our multidimensional, weightsorted tree!
    $recordsTree     = $treeManager->getTree( $records );
    // here we have this tree slapped into a one-dimensional sorted, indented list
    $recordsSlapped  = $treeManager->slapTree( $records );
    // and vice versa!
    $recordsTree     = $treeManager->getTree( $recordsSlapped );
    // lets view our tree in text/html!
    foreach( $recordsSlapped as $node )
      echo "{$node['title_menu_indent']}\n";

### Output ###


    /root A
       / child 1
       / child 2
    /root B
       / child Y
          / child Z

### Explanation ###

Obviously the class is responding to a naming convention for columns (`id` / `parent_id` / `weight` ).
But..it is possible to pass alternative naming conventions as optional arguments to the function.

### Why this class ###

This class which makes life easier when it comes to storing/retrieving hierarchical
arrays (trees) from the database. When you use this, you will be saved from
lots of work.

the idea is to do two-way conversion of tree's and indented lists easily.
Why? So you can easily store the structure in the database, and easily render
this structure into a html selectionbox/menus etc. Think of it as some kind of
'serialize/unserialize' function, but with having the search-benefits of SQL.
I hope you have fun with these trees!


### Example: from MySQL to PHP ###

Suppose this is our datastructure (from SQL/PHP).
  

    $records      = array(  0 => array(  "id"        => 23,
                                         "parent_id" => 0,
                                         "title_menu" => "root A",
                                         "weight"    => 1 ),
                            5 => array(  "id"        => 24,
                                         "parent_id" => 23,
                                         "title_menu" => "child 2",
                                         "weight"    => 3 ),
                            2 => array(  "id"        => 25,
                                         "parent_id" => 0,
                                         "title_menu" => "root B",
                                         "weight"    => 1 ),
                            3 => array(  "id"        => 26,
                                         "parent_id" => 25,
                                         "title_menu" => "child Y",
                                         "weight"    => 1 ),
                            4 => array(  "id"        => 27,
                                         "parent_id" => 26,
                                         "title_menu" => "child Z",
                                         "weight"    => 1 ),
                            1 => array(  "id"        => 24,
                                         "parent_id" => 23,
                                         "title_menu" => "child 1",
                                         "weight"    => 1 )
                          );
    // convert to multidimensional weight-sorted array
    $recordsTree    = getTree( $records );
    print_r($recordsTree);

### Output ###

    Array(
        [0] => Array
            (
                [id] => 23
                [parent_id] => 0
                [title_menu] => root A
                [weight] => 1
                [children] => Array
                    (
                        [1] => Array
                            (
                                [id] => 24
                                [parent_id] => 23
                                [title_menu] => child 1
                                [weight] => 1
                                [children] => Array
                                    (
                                    )

                            )

                        [3] => Array
                            (
                                [id] => 24
                                [parent_id] => 23
                                [title_menu] => child 2
                                [weight] => 3
                                [children] => Array
                                    (
                                    )

                            )

                    )

            )

        [2] => Array
            (
                [id] => 25
                [parent_id] => 0
                [title_menu] => root B
                [weight] => 1
                [children] => Array
                    (
                        [1] => Array
                            (
                                [id] => 26
                                [parent_id] => 25
                                [title_menu] => child Y
                                [weight] => 1
                                [children] => Array
                                    (
                                        [1] => Array
                                            (
                                                [id] => 27
                                                [parent_id] => 26
                                                [title_menu] => child Z
                                                [weight] => 1
                                                [children] => Array
                                                    (
                                                    )

                                            )

                                    )

                            )

                    )

            )

    )

### Example: from hierarchical to records ###


    // convert to indented onedimensional weight-sorted array
    $recordsSlapped = slapTree( $recordsTree);
    foreach($recordsSlapped as $record )
      echo $record['menu_title_indent'] . '\n';
    print_r($recordsSlapped);

### Output ###


    /root A
       / child 1
       / child 2
    /root B
       / child Y
          / child Z
    Array
    (
        [0] => Array
            (
                [id] => 23
                [parent_id] => 0
                [title_menu] => root A
                [weight] => 1
                [indent] => 0
                [title_menu_indent] => /root A
                [title_menu_path] => /root A
            )

        [1] => Array
            (
                [id] => 24
                [parent_id] => 23
                [title_menu] => child 1
                [weight] => 1
                [indent] => 3
                [title_menu_path] => /root A/child 1
                [title_menu_indent] =>    / child 1
            )

        [2] => Array
            (
                [id] => 24
                [parent_id] => 23
                [title_menu] => child 2
                [weight] => 3
                [indent] => 3
                [title_menu_path] => /root A/child 2
                [title_menu_indent] =>    / child 2
            )

        [3] => Array
            (
                [id] => 25
                [parent_id] => 0
                [title_menu] => root B
                [weight] => 1
                [indent] => 0
                [title_menu_indent] => /root B
                [title_menu_path] => /root B
            )

        [4] => Array
            (
                [id] => 26
                [parent_id] => 25
                [title_menu] => child Y
                [weight] => 1
                [indent] => 3
                [title_menu_path] => /root B/child Y
                [title_menu_indent] =>    / child Y
            )

        [5] => Array
            (
                [id] => 27
                [parent_id] => 26
                [title_menu] => child Z
                [weight] => 1
                [indent] => 6
                [title_menu_path] => /root B/child Y/child Z
                [title_menu_indent] =>       / child Z
            )

    )

### Example: and vice versa ###


    $recordsTree     = getTree( $recordsSlapped );
    print_r($recordsTree);


### Output: ###



    Array
    (
        [0] => Array
            (
                [id] => 23
                [parent_id] => 0
                [title_menu] => root A
                [weight] => 1
                [indent] => 0
                [title_menu_indent] => /root A
                [title_menu_path] => /root A
                [children] => Array
                    (
                        [1] => Array
                            (
                                [id] => 24
                                [parent_id] => 23
                                [title_menu] => child 1
                                [weight] => 1
                                [indent] => 3
                                [title_menu_path] => /root A/child 1
                                [title_menu_indent] =>    / child 1
                                [children] => Array
                                    (
                                    )

                            )

                        [3] => Array
                            (
                                [id] => 24
                                [parent_id] => 23
                                [title_menu] => child 2
                                [weight] => 3
                                [indent] => 3
                                [title_menu_path] => /root A/child 2
                                [title_menu_indent] =>    / child 2
                                [children] => Array
                                    (
                                    )

                            )

                    )

            )

        [3] => Array
            (
                [id] => 25
                [parent_id] => 0
                [title_menu] => root B
                [weight] => 1
                [indent] => 0
                [title_menu_indent] => /root B
                [title_menu_path] => /root B
                [children] => Array
                    (
                        [1] => Array
                            (
                                [id] => 26
                                [parent_id] => 25
                                [title_menu] => child Y
                                [weight] => 1
                                [indent] => 3
                                [title_menu_path] => /root B/child Y
                                [title_menu_indent] =>    / child Y
                                [children] => Array
                                    (
                                        [1] => Array
                                            (
                                                [id] => 27
                                                [parent_id] => 26
                                                [title_menu] => child Z
                                                [weight] => 1
                                                [indent] => 6
                                                [title_menu_path] => /root B/child Y/child Z
                                                [title_menu_indent] =>       / child Z
                                                [children] => Array
                                                    (
                                                    )

                                            )

                                    )

                            )

                    )

            )

    )

### Download ###

Download <a href="res/treemanager.zip">here</a>
