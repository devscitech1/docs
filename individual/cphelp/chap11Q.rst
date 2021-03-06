


Chapter 11: Review Questions
============================

::

    
     1. Given the following class and sample program:
    
    //
    //  list.h  - a singly linked list
    //
    #include 
    #include 
    
    class List
    {
    public:
        List() { head = NULL; }
        List( char *str );
        ~List() { release(); }
        int getLength( void );
        void append( List& nlst );
        void add( char *str );   // adds to front of list
        void delete( void )
        {
             ListEntry *temp = head;
             current = head = head->next;
             delete temp;
        }
        int search( char *str );
        ListEntry *getFirst( void )
        {
             current = head;
             return head;
        }
        ListEntry *getNext( void )
        {
        ListEntry *temp = current;
             current = current->next;
             return temp;
        }
        void printList( void );
        void release( void );
    
    private:
    
        typedef
             struct list_entry
             {
                  list_entry *next;
                  char *data;
    
             } ListEntry;
    
        ListEntry *head     // head of list
                  , *current     // current node in list
                  ;
    };
    //
    //  list.cpp
    //
    List::List( char *str )
    {
        // code this
    }
    
    int List::getLength( void )
    {
        // code this
    }
    
    void List::append( List& nlst )
    {
        // code this
    }
    
    void List::add( char *str )
    {
        ListEntry *temp = new ListEntry;   // new element
    
        temp->next = head;
        temp->data = new char[strlen(str)+1];
        strcpy( temp->data, str );
        current = head = temp;
    }
    
    void List::printList( void )
    {
        ListEntry *temp = head;
    
        cout << "********* Beginning of List ***********" << endl;
        while ( temp != NULL )
        {
             cout << temp->data << endl;
             temp = temp->next;
        }
        cout << "********* End of List ****************" << endl;
    }
    
    int List::search( char *str )
    {
        // code this
    }
    
    void List::release( void )
    {
        while ( head != NULL )
             del();
    }
    
    int main()
    {
    List *p;
        {
             List w;
    
             w.add( "First" );
             w.add( "Second" );
             w.add( "Third" );
             w.add( "Fourth" );
             w.printList();
             cout << "\nThere are " 
                  << w.getLength() 
                  << " items in the list."
                  << endl;
             cout << "Searching for Second in list. " << endl;
             w.search( "Second" ) ? cout << "\tFound Match " << endl
                                 : cout << "\tMatch Not Found" << endl;
             w.delete();
             w.printList();
             p = 
             p->printList();
             cout << "\nThere are "
                  << w.getLength()
                  << " items in the list."
                  << endl;
             cout << "Searching for Fourth in list. " << endl;
             w.search( "Fourth" ) ? cout << "\tFound Match " << endl
                                 : cout << "\tMatch Not Found" << endl;
    
        }
        p->printList();
    //
    //  another List
    //
    List list2("Item #1");
        list2.add( "Item #2" );
        list2.add( "Item #3" );
        list2.add( "Item #4" );
        list2.add( "Item #5" );
        list2.printList();
        cout << "\nThere are "
             << list2.getLength()
             << " items in the list."
             << endl;
    //
    //  create another list
    //
    List list3;
        list3.add( "jim" );
        list3.add( "mary" );
        list3.add( "david" );
        list3.add( "laura" );
        list3.pr_list();
        //
        //   append one list to another
        //
        list3.append( list2 );
        list3.printList();
    }
    
     1. What happens upon exit from the inner block?
    
    
    
     2. Code the following member functions:
    
        A. // List constructor whose initializer is a character array
           // that is the value held at the first element of the list
           List::List( char *str );
    
    
        B. // length returns the length of the list, number of nodes
           int List::getLength( void );
    
    
        C. // return true if a match is found, false if not
           int List::search( char *str );
    
    
     3. Write a member function  **append** that will add a 
        list to the rear of the existing list, then clear the 
        list passed by zeroing the head.
    
        void List::append( List& nlst );
    
    Given the following class implementation:
    //
    //  clock.cpp - implement a clock class and example program
    //
    #include 
    
    class Clock
    {
    
    public:
        Clock( unsigned int i )
        {
             tot_secs = i;
             secs = tot_secs % 60;
             mins = (tot_secs / 60 ) % 60;
             hours = (tot_secs / 3600 ) % 24;
             days = tot_secs / 86400;
        }
        void tick();   // add one second
    
        friend Clock& operator++(Clock& ck);
        friend ostream& operator<<( ostream& out, Clock& x);
    
    private:
        unsigned int
             tot_secs
             , secs
             , mins
             , hours
             , days
             ;
        void print( void ); // formatted printout
    
    };
    
    void Clock::tick( void )
    {
        // code this
    }
    
    void Clock::print( void )
    {
        cout << days << "d : " << hours << " h : "
             << mins << "m : " << secs << " s" << endl;
    }
    
    Clock& operator++(Clock& ck)
    {
        // code this
    }
    
    ostream& operator<<( ostream& out, Clock& x)
    {
    }
    
    int main()
    {
    Clock t1(59), t2(172799);
    
        cout << "Initial times are " << endl;
        cout << t1;
        cout << t2;
        ++t1;
        ++t2;     // t1++ or t2++ are the same
        cout << "After one second - times are " << endl;
        cout << t1;
        cout << t2;
    }
    
     4. A. Implement the following method:
    
           void tick();   // add one second
    
    
        B. Implement the following method:
    
           friend Clock& operator++(Clock& ck);
    
    
        C. Define the prototype for the above method and 
           implement the method as an inline member function 
           and not as a friend function.
    
    
        D. Implement the following method: 
    
           friend ostream& operator<<( ostream& out, Clock& x);
    
    




