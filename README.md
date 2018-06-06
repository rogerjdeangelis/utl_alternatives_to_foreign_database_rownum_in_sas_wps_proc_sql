# utl_alternatives_to_foreign_database_rownum_in_sas_wps_proc_sql
Alternatives to foreign database rownum in SAS/WPS proc sql.  Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.

    Alternatives to foreign database rownum in SAS/WPS proc sql

    github
    https://github.com/rogerjdeangelis/utl_alternatives_to_foreign_database_rownum_in_sas_wps_proc_sql

    see
    https://communities.sas.com/t5/Base-SAS-Programming/PROC-SQL/m-p/467975

    KurtBremser Profile
    https://communities.sas.com/t5/user/viewprofilepage/user-id/11562

     1. from sashelp.class(obs=10)
     2. Reset inobs=10
     3. Outobs=10
     4. options obs=10
     5. Monotonic
     6. With a view


    1. from sashelp.class(obs=10)
    -----------------------------

    proc sql;
      create
         table want as
      select
         *
      from
         sashelp.class(obs=10)
    ;quit;


    2. Reset inobs=10
    -----------------

    proc sql;
      reset inobs=10;
      create
         table want as
      select
         *
      from
         sashelp.class
    ;quit;


    3. Outobs=10
    ------------

    proc sql outobs=10;
      create
         table want as
      select
         *
      from
         sashelp.class
    ;quit;


    4. options obs=10

    options obs=10;


    5. Monotonic
    -----------

    proc sql;
      create
         table want (drop=count) as
      select
         *
        ,monotonic() as count
      from
         sashelp.class
      having
         count < 11
    ;quit;


    6. With a view
    ---------------

    data cut10/view=cut10;
    set sashelp.class (obs=10);
    run;quit;


    proc sql outobs=10;
      create
         table want as
      select
         *
      from
         cut10
    ;quit;
