# utl-keep-variable-namess-that-contain-a-specified-substring
Keep variable names that contain a specified substring
    Keep variable names that contain a specified substring

    I want to keep variable name and any other variable name that contains the string 'eight'

    github
    https://tinyurl.com/rpuj9wg
    https://github.com/rogerjdeangelis/utl-keep-variable-namess-that-contain-a-specified-substring

    SAS Forum
    https://tinyurl.com/s8smadh
    https://communities.sas.com/t5/SAS-Programming/Keep-specific-varaibles-from-a-list/m-p/634866

    macros
    https://tinyurl.com/y9nfugth
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories
    *_                   _
    (_)_ __  _ __  _   _| |_
    | | '_ \| '_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    ;

    data hav1st;
      retain Truck_weight "20907" name  "Jones" height1 72 weight2  180  sex "M" age 54;
    run;quit;

    data hav2nd;
      retain CAR_Weight "50301" name "Smith" heighta 72 tot_weight  180  sex "M" age 54;
    run;quit;


    WORK.HAV1ST total obs=1

     Variables in Creation Order

       Variable        Type    Len

       TRUCK_WEIGHT    Char      5
       NAME            Char      5
       HEIGHT1         Num       8
       WEIGHT2         Num       8
       SEX             Char      1
       AGE             Num       8



    WORK.HAV2ND total obs=1

      Variables in Creation Order

      Variable        Type    Len

      CAR_WEIGHT      Char      5
      NAME            Char      5
      HEIGHTA         Num       8
      TOT_WEIGHT      Num       8
      SEX             Char      1
      AGE             Num       8

    *           _
     _ __ _   _| | ___  ___
    | '__| | | | |/ _ \/ __|
    | |  | |_| | |  __/\__ \
    |_|   \__,_|_|\___||___/

    ;


           HAV1ST                              WANT1ST
           ======                  |           =======
    Variable        Type    Len    |    Variable        Type    Len
                                   |
    TRUCK_WEIGHT    Char      5    |    TRUCK_WEIGHT    Char      5
    NAME            Char      5    |    NAME            Char      5
    HEIGHT1         Num       8    |    HEIGHT1         Num       8
    WEIGHT2         Num       8    |    WEIGHT2         Num       8
    SEX             Char      1    |
    AGE             Num       8    |

           HAV2nd                              WANT2nd
           ======                  |           =======
    Variable        Type    Len    |    Variable        Type    Len
                                   |
    CAR_WEIGHT      Char      5    |    TRUCK_WEIGHT    Char      5
    NAME            Char      5    |    NAME            Char      5
    HEIGHTA         Num       8    |    HEIGHT1         Num       8
    TOT_WEIGHT      Num       8    |    WEIGHT2         Num       8
    SEX             Char      1    |
    AGE             Num       8    |

    *            _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| '_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    ;

            WANT1ST
            =======
     Variable        Type    Len

     TRUCK_WEIGHT    Char      5
     NAME            Char      5
     HEIGHT1         Num       8
     WEIGHT2         Num       8



            WANT2nd
            =======
     Variable        Type    Len

     TRUCK_WEIGHT    Char      5
     NAME            Char      5
     HEIGHT1         Num       8
     WEIGHT2         Num       8


     _ __  _ __ ___   ___ ___  ___ ___
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    ;

    data want1st;
      set hav1st(keep=name %utl_varlist(hav1st,prx=/eight/i));
    run;quit;


    data want2nd;
      set hav1st(keep=name %utl_varlist(hav1st,prx=/eight/i));
    run;quit;

