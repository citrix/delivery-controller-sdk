# about_Analytics_Filtering
## TOPIC
    XenDesktop - Advanced Dataset Filtering 

## SHORT DESCRIPTION
    Describes the common filtering options for XenDesktop cmdlets. 

## LONG DESCRIPTION
    Some cmdlets operate on large quantities of data and, to reduce the 
    overhead of sending all of that data over the network, many of the Get- 
    cmdlets support server-side filtering of the results. 

    The conventional way of filtering results in PowerShell is to pipeline 
    them into Where-Object, Select-Object, and Sort-Object, for example: 

      Get-<Noun> | Where { $_.Size = 'Small' } | Sort 'Date' | Select -First 10 

    However, for most XenDesktop cmdlets the data is stored remotely and it 
    would be slow and inefficient to retrieve large amounts of data over the 
    network and then discard most of it. Instead, many of the Get- cmdlets 
    provide filtering parameters that allow results to be processed 
    on the server, returning only the required results. 

    You can filter results by most object properties using parameters 
    derived from the property name. You can also sort results or limit them 
    to a specified number of records: 

      Get-<Noun> -Size 'Small' -SortBy 'Date' -MaxRecordCount 10 

    You can express more complex filter conditions using a syntax and set of 
    operators very similar to those used by PowerShell expressions. 

    Those cmdlets that support filtering have the following common parameters: 

    -MaxRecordCount <int> 
        Specifies the maximum number of results to return. 
        For example, to return only the first nine results use: 

          Get-<Noun> -MaxRecordCount 9 

        If not specified, only the first 250 records are returned, and if more 
        are available, a warning is produced: 

        WARNING: Only first 250 records returned. Use -MaxRecordCount to 
        retrieve more. 

        You can suppress this warning by using -WarningAction or by specifying 
        a value for -MaxRecordCount. 

        To retrieve all records, specify a large number for -MaxRecordCount. 
        As the value is an integer, you can use the following: 

          Get-<Noun> -MaxRecordCount [int]::MaxValue 

    -ReturnTotalRecordCount [<SwitchParameter>] 
        When specified, this causes the cmdlet to output an error record 
        containing the number of records available. This error record is 
        additional information and does not affect the objects written to the 
        output pipeline. For example: 

          Get-<Noun> -MaxRecordCount 9 -ReturnTotalRecordCount 
          .... 

          Get-<Noun> : Returned 9 of 10 items 
          At line:1 char:18 
          + Get-<Noun> <<<<  -MaxRecordCount 9 -ReturnTotalRecordCount 
          + CategoryInfo          : OperationStopped: (:) [Get-<Noun>], PartialDataException 
          + FullyQualifiedErrorId : PartialData,Citrix.<SDKName>.SDK.Get<Noun> 

        The count can be accessed using the TotalAvailableResultCount property: 

          $count = $error[0].TotalAvailableResultCount 

    -Skip <int> 
        Skips the specified number of records before returning results. 
        Also reduces the count returned by -ReturnTotalRecordCount. 

    -SortBy <string> 
        Sorts the results by the specified list of properties. The list is a 
        set of property names separated by commas, semi-colons, or spaces. 
        Optionally, prefix each name with a + or - to indicate ascending or 
        descending order, respectively. Ascending order is assumed if no 
        prefix is present. 

        Sorting occurs before -MaxRecordCount and -Skip parameters are 
        applied. For example, to sort by Name and then by Count (largest first) 
        use: 

          -SortBy 'Name,-Count' 

        By default, sorting by an enumeration property uses the numeric value 
        of the elements. You can specify a different sort order by qualifying 
        the name with an ordered list of elements or their numeric values, 
        or <null> to indicate the placement of null values. 
        Elements not mentioned are placed at the end in their numeric order. 
        For example, to sort by two different enums and then by the object id: 

          -SortBy 'MyState(StateC,<null>,StateA,StateB),Another(0,3,2,1),Id' 

    -Filter <String> 
        This parameter lets you specify advanced filter expressions, and 
        supports combination of conditions with -and and -or, and grouping 
        with braces. For example: 

          Get-<Noun> -Filter 'Name -like "High*" -or (Priority -eq 1 -and Severity -ge 2)' 

        The syntax is close enough to PowerShell syntax that you can use 
        script blocks in most cases. This can be easier to read as it reduces 
        quoting: 

          Get-<Noun> -Filter { Count -ne $null } 

        The full -Filter syntax is provided below. 

## EXAMPLES
    Filtering by strings performs a case-insensitive wildcard match. 
    Separate parameters are combined with an implicit -and operator. 
    Normal PowerShell quoting rules apply, so you can use single or double 
    quotes, and omit the quotes altogether for many strings. The order of 
    parameters does not make any difference. The following are equivalent: 

      Get-<Noun> -Company Citrix -Product Xen* 
      Get-<Noun> -Company "citrix" -Product '[X]EN*' 
      Get-<Noun> -Product "Xen*" -Company "CITRIX" 
      Get-<Noun> -Filter { Company -eq 'Citrix' -and Product -like 'Xen*' } 

    See about_Quoting_Rules and about_Wildcards for details about PowerShell 
    handling of quotes and wildcards. 

    To avoid wildcard matching or include quote characters, you can escape 
    the wildcards using the normal PowerShell escape mechanisms (see 
    about_Escape_Characters), or switch to a filter expression and the -eq 
    operator: 

      Get-<Noun> -Company "Abc[*]"                 # Matches Abc* 
      Get-<Noun> -Company "Abc`*"                  # Matches Abc* 
      Get-<Noun> -Filter { Company -eq "Abc*" }    # Matches Abc* 
      Get-<Noun> -Filter { Company -eq "A`"B`'C" } # Matches A"B'C 

    Simple filtering by numbers, booleans, and TimeSpans perform direct 
    equality comparisons, although if the value is nullable you can also 
    search for null values. Here are some examples: 

      Get-<Noun> -Uid 123 
      Get-<Noun> -Enabled $true 
      Get-<Noun> -Duration 1:30:40 
      Get-<Noun> -NullableProperty $null 

    More comparisons are possible using advanced filtering with -Filter: 

      Get-<Noun> -Filter 'Capacity -ge 10gb' 
      Get-<Noun> -Filter 'Age -ge 20 -and Age -lt 40' 
      Get-<Noun> -Filter 'VolumeLevel -like "[123]"' 
      Get-<Noun> -Filter 'Enabled -ne $false' 
      Get-<Noun> -Filter 'NullableProperty -ne $null' 

    You can check boolean values without an explicit comparison operator, 
    and you can also combine them with -not: 

      Get-<Noun> -Filter 'Enabled'      # Equivalent to 'Enabled -eq $true' 
      Get-<Noun> -Filter '-not Enabled' # Equivalent to 'Enabled -eq $false' 

    See about_Comparison_Operators for an explanation of the operators, but 
    note that only a subset of PowerShell operators are supported (-eq, -ne, 
    -gt, -ge, -lt, -le, -like, -notlike, -in, -notin, -contains, -notcontains). 

    Enumeration values can either be specified using typed values or the 
    string name of the enumeration value: 

      Get-<Noun> -Shape [Shapes]::Square 
      Get-<Noun> -Shape Circle 

    With filter expressions, typed values can be specified with simple 
    variables or quoted strings. They also support enumerations with wildcards: 

      $s = [Shapes]::Square 
      Get-<Noun> -Filter { Shape -eq $s -or Shape -eq "Circle" } 
      Get-<Noun> -Filter { Shape -like 'C*' } 

    By their nature, floating point values, DateTime values, and TimeSpan 
    values are best suited to relative comparisons rather than just equality. 
    DateTime strings are converted using the locale and time zone of the user 
    device, but you can use ISO8601 format strings (YYYY-MM-DDThh:mm:ss.sTZD) 
    to avoid ambiguity. You can also use standard PowerShell syntax to 
    create these values: 

      Get-<Noun> -Filter { StartTime -ge "2010-08-23T12:30:00.0Z" } 
      $d = [DateTime]"2010-08-23T12:30:00.0Z" 
      Get-<Noun> -Filter { StartTime -ge $d } 
      $d = (Get-Date).AddDays(-1) 
      Get-<Noun> -Filter { StartTime -ge $d } 

    Relative times are quite common and, when using filter expressions, 
    you can also specify DateTime values using a relative format: 

      Get-<Noun> -Filter { StartTime -ge '-2' }         # Two days ago 
      Get-<Noun> -Filter { StartTime -ge '-1:30' }      # Hour and a half ago 
      Get-<Noun> -Filter { StartTime -ge '-0:0:30' }    # 30 seconds ago 

  ARRAY PROPERTIES 
    When filtering against list or array properties, simple parameters perform 
    a case-insensitive wildcard match against each of the members. With filter 
    expressions, you can use the -contains and -notcontains operators. Unlike 
    PowerShell, these perform wildcard matching on strings. 
    Note that for array properties the naming convention is for the returned 
    property to be plural, but the parameter used to search for any match is 
    singular. The following are equivalent (assuming Users is an array 
    property): 

      Get-<Noun> -User Fred* 
      Get-<Noun> -Filter { User -like "Fred*" } 
      Get-<Noun> -Filter { Users -contains "Fred*" } 

    You can also use the singular form with -Filter to search using other 
    operators: 

      # Match if any user in the list is called "Frederick" 
      Get-<Noun> -Filter { User -eq "Frederick" } 
      # Match if any user in the list has a name alphabetically below 'F' 
      Get-<Noun> -Filter { User -lt 'F' } 

  COMPLEX EXPRESSIONS 
    When matching against multiple values, you can use a sequence of 
    comparisons joined with -or operators, or you can use -in and -notin: 

      Get-<Noun> -Filter { Shape -eq 'Circle' -or Shape -eq 'Square' } 
      $shapes = 'Circle','Square' 
      Get-<Noun> -Filter { Shape -in $shapes } 
      $sides = 1..4 
      Get-<Noun> -Filter { Sides -notin $sides } 

    Braces can be used to group complex expressions, and override the default 
    left-to-right evaluation of -and and -or. You can also use -not to invert 
    the sense of any sub-expression: 

      Get-<Noun> -Filter { Size -gt 4 -or (Color -eq 'Blue' -and Shape -eq 'Circle') } 
      Get-<Noun> -Filter { Sides -lt 5 -and -not (Color -eq 'Blue' -and Shape -eq 'Circle') } 

  PAGING 
    The simplest way to page through data is to use the -Skip and 
    -MaxRecordCount parameters. So, to read the first three pages of data with 
    10 records per page, use: 

      Get-<Noun> -Skip 0  -MaxRecordCount 10 <other filtering criteria> 
      Get-<Noun> -Skip 10 -MaxRecordCount 10 <other filtering criteria> 
      Get-<Noun> -Skip 20 -MaxRecordCount 10 <other filtering criteria> 

    You must include the same filtering criteria on each call, and 
    ensure that the data is sorted consistently. 

    The above approach is often acceptable, but as each call performs an 
    independent query, data changes can result in records being skipped or 
    appearing twice. One approach to improve this is to sort by a unique id 
    field and then start the search for the next page at the unique id after 
    the last unique id of the previous page. For example: 

      # Get the first page 
      Get-<Noun> -MaxRecordCount 10 -SortBy SerialNumber 

      SerialNumber  ... 
      ------------  --- 
      A120004 
      A120007 
      ... 7 other records ... 
      A120900 

      # Get the next page 
      Get-<Noun> -MaxRecordCount 10 -Filter { FirstName -gt 'A120900' } 

      SerialNumber  ... 
      ------------  --- 
      A120901 
      B220000 
      ... 

## FILTER SYNTAX DEFINITION

    <Filter>        ::= <ScriptBlock> | <ComponentList> 

    <ScriptBlock>   ::= "{" <ComponentList> "}" 

    <ComponentList> ::= <Component> <AndOrOperator> <ComponentList> | 
                        <Component> 

    <Component>     ::= <NotOperator> <Factor> | 
                        <Factor> 

    <Factor>        ::= "(" <ComponentList> ")" | 
                        <PropertyName> <ComparisonOperator> <Value> | 
                        <PropertyName> 

    <AndOrOperator> ::= "-and" | "-or" 

    <NotOperator>   ::= "-not" | "!" 

    <ComparisonOperator> 
                    ::= "-eq" | "-ne" | "-le" | "-ge" | "-lt" | "-gt" | 
                        "-like" | "-notlike" | "-contains" | "-notcontains" | 
                        "-in" | "-notin" 

    <PropertyName>  ::= <simple name of property> 

    <Value>         ::= <string literal>  | <numeric literal> | 
                        <scalar variable> | <array variable>  | 
                        "$null" | "$true" | "$false" 

    Numeric literals support decimal and hexadecimal literals, with optional 
    multiplier suffixes (kb, mb, gb, tb, pb). 

    Dates and times can be specified as string literals. The current culture 
    determines what formats are accepted. To avoid any ambiguity, use strings 
    formatted to the ISO8601 standard. If not specified, the current time zone 
    is used. 

    Relative date-time string literals are also supported, using a minus sign 
    followed by a TimeSpan. For example, "-1:30" means 1 hour and 30 minutes 
    ago. 
