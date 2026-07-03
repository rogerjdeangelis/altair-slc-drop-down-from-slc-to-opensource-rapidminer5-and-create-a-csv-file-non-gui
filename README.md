# altair-slc-drop-down-from-slc-to-opensource-rapidminer5-and-create-a-csv-file-non-gui
Altair SLC drop-down from slc to Open Source RapidMiner5 and create a csv file non gui
     
    Altair SLC drop-down from slc to opensource rapidminer5 and create a csv file non gui

    Too long to post, see
    https://github.com/rogerjdeangelis/altair-slc-drop-down-from-slc-to-opensource-rapidminer5-and-create-a-csv-file-non-gui
    
    The RapidMiner XML program creates a dataset and converts it to a csv in c:/temp/generated_data.csv

    You can download rapidminer 5 from
    https://sourceforge.net/directory/windows/?q=rapidminer
    or
    https://1drv.ms/u/c/bb0f3c4c9b1dc58b/IQCANDQmp-gmSZSKcQ2pglltAUCInDEbugcFoCBr6CjhL7Q?e=z5Pfzs

    CONTENTS

       1 Input & process (input is data is generated within the process)
       2 Simple commad line
       3 Drop down to rapidminer macros (on end)
         macros supports input and output macro variables
         also at
         https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories

    You can use the GUI, there are several ways to open the gui.

    C:\Program Files (x86)\Rapid-I\RapidMiner5\rapidminer.exe
    Go to
    C:\Program Files (x86)\Rapid-I\RapidMiner5\lib\rapdminer.jar
    select java(Tm)
    There appear to be over ways (see C:\Program Files (x86)\Rapid-I\RapidMiner5\scripts)

    Rapidminer 5 is 32 bit.

    I don't think you need java, because jre is included in the install  (nice like the slc)

    Simple install, I did create a newlocalrepository folder, but I don't think it is needed for this example below.

    The xml code creates a dataset and converts it to a csv in c:/temp/generated_data.csv'

    LICENSE

     *  RapidMiner

     *

     *  Copyright (C) 2001-2011 by Rapid-I and the contributors

     *

     *  Complete list of developers available at our web site:

     *
    
 *       http://rapid-i.com
    
 *
    
 *  This program is free software: you can redistribute it and/or modify
    
 *  it under the terms of the GNU Affero General Public License as published by
    
 *  the Free Software Foundation, either version 3 of the License, or

     *  (at your option) any later version.
    
 *
    
 *  This program is distributed in the hope that it will be useful,
    
 *  but WITHOUT ANY WARRANTY; without even the implied warranty of
    
 *  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    
 *  GNU Affero General Public License for more details.
    
 *
    
 *  You should have received a copy of the GNU Affero General Public License

     *  along with this program.  If not, see http://www.gnu.org/licenses/.

    /*   _                   _      ___
    / | (_)_ __  _ __  _   _| |_   ( _ )    _ __  _ __ ___   ___ ___  ___ ___
    | | | | `_ \| `_ \| | | | __|  / _ \/\ | `_ \| `__/ _ \ / __/ _ \/ __/ __|
    | | | | | | | |_) | |_| | |_  | (_>  < | |_) | | | (_) | (_|  __/\__ \__ \
    |_| |_|_| |_| .__/ \__,_|\__|  \___/\/ | .__/|_|  \___/ \___\___||___/___/
         _       |_|           _             |_|                         _                 _
      __| |_ __ ___  _ __   __| | _____      ___ __  ___  __ _ _ __   __| |_      _(_) ___| |__
     / _` | `__/ _ \| `_ \ / _` |/ _ \ \ /\ / / `_ \/ __|/ _` | `_ \ / _` \ \ /\ / / |/ __| `_ \
    | (_| | | | (_) | |_) | (_| | (_) \ V  V /| | | \__ \ (_| | | | | (_| |\ V  V /| | (__| | | |
     \__,_|_|  \___/| .__/ \__,_|\___/ \_/\_/ |_| |_|___/\__,_|_| |_|\__,_| \_/\_/ |_|\___|_| |_|
    */

    /*--- WHERE YOU WANT TO SAVE THE CSV ---*/

    %utlfkil(c:\temp\generated_data.csv);

    %let csv = c:\temp\generated_data.csv;

    %slc_rmbegin;
    cards4;
    <?xml version="1.0" encoding="UTF-8" standalone="no"?>
    <process version="5.0">
      <context>
        <input/>
        <output/>
        <macros/>
      </context>
      <operator activated="true" class="process" expanded="true" name="Process">
        <process expanded="true">
          <operator activated="true" class="generate_data" expanded="true" height="60" name="Generate Data" width="90" x="112" y="75">
            <parameter key="number_examples" value="100"/>
            <parameter key="number_of_attributes" value="3"/>
            <parameter key="target_function" value="sum"/>
            <parameter key="attributes_lower_bound" value="-10.0"/>
            <parameter key="attributes_upper_bound" value="10.0"/>
          </operator>
          <operator activated="true" class="write_csv" expanded="true" height="60" name="Write CSV" width="90" x="246" y="75">
            <parameter key="csv_file" value="c:\temp\generated_data.csv"/>
            <parameter key="column_separator" value=","/>
            <parameter key="write_attribute_names" value="true"/>
          </operator>
          <connect from_op="Generate Data" from_port="output" to_op="Write CSV" to_port="input"/>
          <connect from_op="Write CSV" from_port="through" to_port="result 1"/>
        </process>
      </operator>
    </process>
    ;;;;
    %slc_rmend(,resolve=Y); /*--- RESOLVES THE OUTPUT LOCATION ---*/

    /*           _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| `_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    */

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*  "att1","att2","att3","label"                                                                                          */
    /*  2.467612009982549,7.2671269538811885,1.2924127751628518,11.02715173902659                                             */
    /*  -8.624734314791924,-5.589923335093689,-0.30679312206221354,-14.521450771947826                                        */
    /*  -6.350916620988873,9.36985643429379,1.2414027313347589,4.260342544639676                                              */
    /*  8.732745593719283,-8.767780617998435,3.85172212001336,3.816687095734208                                               */
    /*  -5.189688812982061,-1.9784922730803967,-6.224623149327426,-13.392804235389884                                         */
    /*  -9.412609914436592,-7.153585749698594,-8.452739809286108,-25.018935473421294                                          */
    /*  -4.695913351021728,-4.3952068813403855,5.303776511812439,-3.787343720549675                                           */
    /* ...                                                                                                                    */
    /**************************************************************************************************************************/

    /*
    | | ___   __ _
    | |/ _ \ / _` |
    | | (_) | (_| |
    |_|\___/ \__, |
             |___/
    */

    1                                          Altair SLC           15:24 Friday, July  3, 2026

    NOTE: Copyright 2002-2025 World Programming, an Altair Company
    NOTE: Altair SLC 2026 (05.26.01.00.000758)
          Licensed to Roger DeAngelis
    NOTE: This session is executing on the X64_WIN11PRO platform and is running in 64 bit mode

    NOTE: AUTOEXEC processing beginning; file is C:\wpsoto\autoexec.sas
    NOTE: Library workx assigned as follows:
          Engine:        SAS7BDAT
          Physical Name: d:\wpswrkx

    NOTE: Library wpdx assigned as follows:
          Engine:        WPD
          Physical Name: d:\wpswrkx

    NOTE: Library slchelp assigned as follows:
          Engine:        WPD
          Physical Name: C:\Progra~1\Altair\SLC\2026\sashelp


    LOG:  15:24:58
    NOTE: 1 record was written to file PRINT

    NOTE: The data step took :
          real time : 0.031
          cpu time  : 0.000


    NOTE: Format num2mis output
    NOTE: Format $chr2mis output
    NOTE: Procedure format step took :
          real time : 0.015
          cpu time  : 0.000


    NOTE: AUTOEXEC processing completed

    1          %slc_rmbegin;
    2         cards4;

    NOTE: The file 'c:\temp\rm_pgmx.xml' is:
          Filename='c:\temp\rm_pgmx.xml',
          Owner Name=SLC\suzie,
          File size (bytes)=0,
          Create Time=13:57:56 Jul 03 2026,
          Last Accessed=15:24:57 Jul 03 2026,
          Last Modified=15:24:57 Jul 03 2026,
          Lrecl=32767, Recfm=V

    NOTE: 26 records were written to file 'c:\temp\rm_pgmx.xml'
          The minimum record length was 80
          The maximum record length was 130
    NOTE: The data step took :
          real time : 0.000
          cpu time  : 0.000


    3         <?xml version="1.0" encoding="UTF-8" standalone="no"?>
    4         <process version="5.0">
    5           <context>
    6             <input/>
    7             <output/>
    8             <macros/>
    9           </context>
    10          <operator activated="true" class="process" expanded="true" name="Process">
    11            <process expanded="true">
    12              <operator activated="true" class="generate_data" expanded="true" height="60" name="Generate Data" width="90" x="112" y="75">
    13                <parameter key="number_examples" value="100"/>
    14                <parameter key="number_of_attributes" value="3"/>
    15                <parameter key="target_function" value="sum"/>
    16                <parameter key="attributes_lower_bound" value="-10.0"/>
    17                <parameter key="attributes_upper_bound" value="10.0"/>
    18              </operator>
    19              <operator activated="true" class="write_csv" expanded="true" height="60" name="Write CSV" width="90" x="246" y="75">
    20                <parameter key="csv_file" value="c:\temp\generated_data.csv"/>
    21                <parameter key="column_separator" value=","/>
    22                <parameter key="write_attribute_names" value="true"/>
    23              </operator>
    24              <connect from_op="Generate Data" from_port="output" to_op="Write CSV" to_port="input"/>
    25              <connect from_op="Write CSV" from_port="through" to_port="result 1"/>
    26            </process>
    27          </operator>
    28        </process>
    29        ;;;;
    30        %slc_rmend;

    NOTE: The infile 'c:\temp\rm_pgmx.xml' is:
          Filename='c:\temp\rm_pgmx.xml',
          Owner Name=SLC\suzie,
          File size (bytes)=2237,
          Create Time=13:57:56 Jul 03 2026,
          Last Accessed=15:24:57 Jul 03 2026,
          Last Modified=15:24:57 Jul 03 2026,
          Lrecl=32767, Recfm=V

    NOTE: The file 'c:\temp\rm_pgm.xml' is:
          Filename='c:\temp\rm_pgm.xml',
          Owner Name=SLC\suzie,
          File size (bytes)=0,
          Create Time=14:56:52 Jul 03 2026,
          Last Accessed=15:24:57 Jul 03 2026,
          Last Modified=15:24:57 Jul 03 2026,
          Lrecl=32767, Recfm=V

    <?xml version="1.0" encoding="UTF-8" standalone="no"?>
    <process version="5.0">
      <context>
        <input/>
        <output/>
        <macros/>
      </context>
      <operator activated="true" class="process" expanded="true" name="Process">
        <process expanded="true">
          <operator activated="true" class="generate_data" expanded="true" height="60" name="Generate Data" width="90" x="112" y="75">
            <parameter key="number_examples" value="100"/>
            <parameter key="number_of_attributes" value="3"/>
            <parameter key="target_function" value="sum"/>
            <parameter key="attributes_lower_bound" value="-10.0"/>
            <parameter key="attributes_upper_bound" value="10.0"/>
          </operator>
          <operator activated="true" class="write_csv" expanded="true" height="60" name="Write CSV" width="90" x="246" y="75">
            <parameter key="csv_file" value="c:\temp\generated_data.csv"/>
            <parameter key="column_separator" value=","/>
            <parameter key="write_attribute_names" value="true"/>
          </operator>
          <connect from_op="Generate Data" from_port="output" to_op="Write CSV" to_port="input"/>
          <connect from_op="Write CSV" from_port="through" to_port="result 1"/>
        </process>
      </operator>
    </process>
    NOTE: 26 records were read from file 'c:\temp\rm_pgmx.xml'
          The minimum record length was 80
          The maximum record length was 130
    NOTE: 26 records were written to file 'c:\temp\rm_pgm.xml'
          The minimum record length was 80
          The maximum record length was 130
    NOTE: The data step took :
          real time : 0.015
          cpu time  : 0.000



    NOTE: The infile rut is:
          Unnamed Pipe Access Device,
          Process=C:\PROGRA~2\Java\jdk1.6.0_45\bin\java.exe -cp C:\PROGRA~2\Rapid-I\RapidMiner5\lib\rapidminer.jar com.rapidminer.RapidMinerCommandLine -f c:\temp\rm_pgm.xml >> c:\temp\rm_pgm.log 2>&1,
          Lrecl=32767, Recfm=V

    NOTE: No records were written to file PRINT

    NOTE: No records were read from file rut
    NOTE: The data step took :
          real time : 1.902
          cpu time  : 0.000



    NOTE: The infile 'c:\temp\rm_pgm.log' is:
          Filename='c:\temp\rm_pgm.log',
          Owner Name=SLC\suzie,
          File size (bytes)=1922,
          Create Time=14:56:52 Jul 03 2026,
          Last Accessed=15:24:59 Jul 03 2026,
          Last Modified=15:24:59 Jul 03 2026,
          Lrecl=32767, Recfm=V

    RapidMiner version 5.2.000, Copyright (C) 2001-2008
    RapidMiner comes with ABSOLUTELY NO WARRANTY; This is free software,
    and you are welcome to redistribute it under certain conditions;
    see license information in the file named LICENSE.
    Jul 3, 2026 3:24:57 PM com.rapid_i.Launcher ensureRapidMinerHomeSet
    INFO: Property rapidminer.home is not set. Guessing.
    Jul 3, 2026 3:24:57 PM com.rapid_i.Launcher ensureRapidMinerHomeSet
    INFO: Trying parent directory of 'C:\PROGRA~2\Rapid-I\RapidMiner5\lib\rapidminer.jar'...gotcha!
    Jul 3, 2026 3:24:57 PM com.rapidminer.tools.ParameterService init
    INFO: Reading configuration resource com/rapidminer/resources/rapidminerrc.
    Jul 3, 2026 3:24:57 PM com.rapid_i.Launcher ensureRapidMinerHomeSet
    INFO: rapidminer.home is 'C:\PROGRA~2\Rapid-I\RapidMiner5'.
    Jul 3, 2026 3:24:59 PM com.rapidminer.parameter.ParameterTypePassword decryptPassword
    WARNING: Password in XML file looks like unencrypted plain text.
    Jul 3, 2026 3:24:59 PM com.rapidminer.tools.jdbc.JDBCProperties <init>
    WARNING: Missing database driver class name for 'ODBC Bridge (e.g. Access)'
    Jul 3, 2026 3:24:59 PM com.rapidminer.tools.jdbc.JDBCProperties registerDrivers
    INFO: JDBC driver ca.ingres.jdbc.IngresDriver not found. Probably the driver is not installed.
    Jul 3, 2026 3:24:59 PM com.rapidminer.tools.jdbc.JDBCProperties registerDrivers
    INFO: JDBC driver oracle.jdbc.driver.OracleDriver not found. Probably the driver is not installed.
    Jul 3, 2026 3:24:59 PM com.rapidminer.tools.WrapperLoggingHandler log
    INFO: No filename given for result file, using stdout for logging results!
    Jul 3, 2026 3:24:59 PM com.rapidminer.Process run
    INFO: Process c:\temp\rm_pgm.xml starts
    Jul 3, 2026 3:24:59 PM com.rapidminer.Process run
    INFO: Process c:\temp\rm_pgm.xml finished successfully after 0 s
    Jul 3, 2026 3:24:59 PM com.rapidminer.RapidMinerCommandLine run
    INFO: Process finished successfully
    NOTE: 28 records were read from file 'c:\temp\rm_pgm.log'
          The minimum record length was 35
          The maximum record length was 98
    NOTE: The data step took :
          real time : 0.016
          cpu time  : 0.000


    31

    NOTE: Submitted statements took :
          real time : 2.118
          cpu time  : 0.078

    /*___        _                 _                                                     _   _ _
    |___ \   ___(_)_ __ ___  _ __ | | ___   ___ ___  _ __ ___  _ __ ___   __ _ _ __   __| | | (_)_ __   ___
      __) | / __| | `_ ` _ \| `_ \| |/ _ \ / __/ _ \| `_ ` _ \| `_ ` _ \ / _` | `_ \ / _` | | | | `_ \ / _ \
     / __/  \__ \ | | | | | | |_) | |  __/| (_| (_) | | | | | | | | | | | (_| | | | | (_| | | | | | | |  __/
    |_____| |___/_|_| |_| |_| .__/|_|\___| \___\___/|_| |_| |_|_| |_| |_|\__,_|_| |_|\__,_| |_|_|_| |_|\___|
                            |_|
    */

    /*--- SAVE XML PROGRAM AT C:/TEMP/CSV.XML ---*/

    data _null_;
     file "c:/temp/csv.xml";
     input;
     put _infile_;
    cards4;
    <?xml version="1.0" encoding="UTF-8" standalone="no"?>
    <process version="5.0">
      <context>
        <input/>
        <output/>
        <macros/>
      </context>
      <operator activated="true" class="process" expanded="true" name="Process">
        <process expanded="true">
          <operator activated="true" class="generate_data" expanded="true" height="60" name="Generate Data" width="90" x="112" y="75">
            <parameter key="number_examples" value="100"/>
            <parameter key="number_of_attributes" value="3"/>
            <parameter key="target_function" value="sum"/>
            <parameter key="attributes_lower_bound" value="-10.0"/>
            <parameter key="attributes_upper_bound" value="10.0"/>
          </operator>
          <operator activated="true" class="write_csv" expanded="true" height="60" name="Write CSV" width="90" x="246" y="75">
            <parameter key="csv_file" value="c:\temp\generated_data.csv"/>
            <parameter key="column_separator" value=","/>
            <parameter key="write_attribute_names" value="true"/>
          </operator>
          <connect from_op="Generate Data" from_port="output" to_op="Write CSV" to_port="input"/>
          <connect from_op="Write CSV" from_port="through" to_port="result 1"/>
        </process>
      </operator>
    </process>
    ;;;;
    run;

    /*--- CREATE THE CSV ---*/

    x "C:\PROGRA~2\Java\jdk1.6.0_45\bin\java.exe -cp C:\PROGRA~2\Rapid-I\RapidMiner5\lib\rapidminer.jar com.rapidminer.RapidMinerCommandLine -f c:\temp\rm_pgm.xml >> c:\temp\rm_pgm.log 2>&1

    /*____       _                       _
    |___ /    __| |_ __ ___  _ __     __| | _____      ___ __   _ __ ___   __ _  ___ _ __ ___  ___
      |_ \   / _` | `__/ _ \| `_ \   / _` |/ _ \ \ /\ / / `_ \ | `_ ` _ \ / _` |/ __| `__/ _ \/ __|
     ___) | | (_| | | | (_) | |_) | | (_| | (_) \ V  V /| | | || | | | | | (_| | (__| | | (_) \__ \
    |____/   \__,_|_|  \___/| .__/   \__,_|\___/ \_/\_/ |_| |_||_| |_| |_|\__,_|\___|_|  \___/|___/
                            |_|
    */

    /*--- SAVE IN YOUR AUTOCALL FOLDER. I USE C:/WPSOTO ---*/

    data _null_;
      input;
      file "c:/wpsoto/slc_rmbegin.sas";
      put _infile_;
    cards4;
    %macro slc_rmbegin;
      %utlfkil(c:/temp/rm_pgm.xml);
      %utlfkil(c:/temp/rm_pgm.log);
      data _null_;
        file "c:/temp/rm_pgmx.xml";
        input;
        put _infile_;
    %mend slc_rmbegin;
    ;;;;
    run;

    data _null_;
      input;
      file "c:/wpsoto/slc_rmend.sas";
      put _infile_;
    cards4;
    %macro slc_rmend(return=,resolve=N);
      run;
      quit;
      data _null_;
        infile "c:/temp/rm_pgmx.xml";
        input;
        file "c:/temp/rm_pgm.xml";
        if upcase(substr("&resolve",1,1))="Y" then
           _infile_=resolve(_infile_);
        put _infile_;
        putlog _infile_;
      run;
      quit;

      * EXECUTE THE PYTHON PROGRAM USING DIRECT PYTHON (NOT CONDA RUN);

      options noxwait noxsync;

      filename rut pipe "C:\PROGRA~2\Java\jdk1.6.0_45\bin\java.exe -cp C:\PROGRA~2\Rapid-I\RapidMiner5\lib\rapidminer.jar com.rapidminer.RapidMinerCommandLine -f c:\temp\rm_pgm.xml >> c:\temp\rm_pgm.log 2>&1";

      data _null_;
        file print;
        infile rut;
        input;
        put _infile_;
        putlog _infile_;
      run;
      quit;

      data _null_;
        infile "c:/temp/rm_pgm.log";
        input;
        putlog _infile_;
      run;
      quit;

      %if "&return" ne "" %then %do;
        filename clp clipbrd;
        data _null_;
          infile clp;
          input;
          putlog "xxxxxx  " _infile_;
          call symputx("&return.",_infile_,"G");
        run;
        quit;
      %end;
    %mend slc_rmend;
    ;;;;
    run;

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
