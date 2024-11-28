+----------------------------------+------------------------+----------+
| ![](vertopal_                    |                        |          |
| 0ef74778e9b344dba38f75b63b38a781 |                        |          |
| /media/image1.png){width="2.4in" |                        |          |
| height="0.5881944444444445in"}   |                        |          |
|                                  |                        |          |
| SCHOOL OF INFORMATION AND        |                        |          |
| TECHNOLOGY                       |                        |          |
+----------------------------------+------------------------+----------+
| NAME: Cruz, Rodolfo Franco P.    | DATE PERFORMED:        |          |
|                                  | 29/08/2024             |          |
+----------------------------------+------------------------+----------+
| Section: IDC2                    | DATE SUBMITTED:        |          |
|                                  | 29/08/2024             |          |
+----------------------------------+------------------------+----------+

# SYSADM1 -- Managing Services in Windows

# Requirement: 

-   A virtual machine running Linux and Windows OS

    **Services** are background processes that run independently of user
    interactions in Windows. They provide essential system functions,
    such as network connectivity, printing, and time synchronization.
    This lab will guide you through the process of managing services
    using the Services app.

# Instructions:  {#instructions .list-paragraph}

1.  Open the Start menu and search for \"Services\"

2.  Familiarize yourself with the columns, including Service Name,
    Display Name, Status, and Startup type.

3.  Right-click on a service and select \"Start\", \"Stop\", or
    \"Restart\". Fill out the table below

  ---------------------------------------------------------------------------------------------------------------------------------------
  **Status**   **Name of Service**         **Screenshot**
  ------------ --------------------------- ----------------------------------------------------------------------------------------------
  Start        Cryptographic Services      ![](vertopal_0ef74778e9b344dba38f75b63b38a781/media/image2.png){width="2.568627515310586in"
                                           height="1.7684798775153105in"}

                                           

  Stop         Application Experience      ![](vertopal_0ef74778e9b344dba38f75b63b38a781/media/image3.png){width="2.9171030183727034in"
                                           height="1.9426268591426072in"}

  Restart      Base Filtering Engine       ![](vertopal_0ef74778e9b344dba38f75b63b38a781/media/image4.png){width="2.952097550306212in"
                                           height="1.6833770778652668in"}

  Pause        Server (local)              ![](vertopal_0ef74778e9b344dba38f75b63b38a781/media/image5.png){width="2.951473097112861in"
                                           height="2.4112970253718284in"}
  ---------------------------------------------------------------------------------------------------------------------------------------

4.  Select five network services, right-click to view its properties.
    Modify the startup setting to Manual.

> **SS**:

  -------------------------------------------------------------------------------------------------------------------------------
  Security Accounts Manager         ![](vertopal_0ef74778e9b344dba38f75b63b38a781/media/image6.png){width="2.946476377952756in"
                                    height="3.3349431321084864in"}
  --------------------------------- ---------------------------------------------------------------------------------------------
  Network Location Awareness        ![](vertopal_0ef74778e9b344dba38f75b63b38a781/media/image7.png){width="2.9888156167979in"
                                    height="3.3578062117235348in"}

  Diagnostic Policy Service         ![](vertopal_0ef74778e9b344dba38f75b63b38a781/media/image8.png){width="2.908875765529309in"
                                    height="3.277912292213473in"}

  Cryptographic Services            ![](vertopal_0ef74778e9b344dba38f75b63b38a781/media/image9.png){width="2.907156605424322in"
                                    height="3.266066272965879in"}
  -------------------------------------------------------------------------------------------------------------------------------

5.  Explore the \"General\", \"Recovery\", and \"Log On\" tabs to
    understand additional service settings.

6.  Create a batch file that will be added as a new service later on.
    Refer to the batch file code below.

> ![](vertopal_0ef74778e9b344dba38f75b63b38a781/media/image10.png){width="4.808325678040245in"
> height="2.0055664916885387in"}

7.  Save the batch file in Z:\\lastname_timer.bat

> ![](vertopal_0ef74778e9b344dba38f75b63b38a781/media/image11.png){width="6.323799212598425in"
> height="0.29170713035870516in"}

8.  Use the sc command to add timer.bat service in the command line
    interface.

> *sc create BatchTimerService binPath= \"path_to_your_batch_file.bat\"
> start= auto*
>
> *net start BatchTimerService*
>
> **Replace path_to_your_batch_file.bat with the actual path to your
> batch file.**

9.  Verify that BatchTimerService has been added to the services.

> **SS:**
> ![](vertopal_0ef74778e9b344dba38f75b63b38a781/media/image12.png){width="4.479792213473316in"
> height="2.000278871391076in"}

10. **Testing the Service:** Now, if you open a new command prompt, you
    should see the timer countdown without requiring your interaction.
    Once the timer finishes, you\'ll see the \"Timer finished!\"
    message.

> **SS:**
> ![](vertopal_0ef74778e9b344dba38f75b63b38a781/media/image13.png){width="5.615367454068242in"
> height="2.1878051181102363in"}![](vertopal_0ef74778e9b344dba38f75b63b38a781/media/image14.png){width="6.105018591426072in"
> height="2.698292869641295in"}

**Rubric**

  ---------------------------------------------------------------------------------------
  **Criteria**      **Excellent       **Good (7)**    **Needs          **Unsatisfactory
                    (10)**                            Improvement      (1)**
                                                      (3)**            
  ----------------- ----------------- --------------- ---------------- ------------------
  Understanding of  Demonstrates a    Shows a solid   Has a basic      Shows little or no
  Services          deep              understanding   understanding of understanding of
                    understanding of  of services,    services, but    services.
                    the concept of    but may lack    may struggle     
                    services, their   some depth in   with specific    
                    roles, and their  specific areas. concepts.        
                    importance in                                      
                    Windows.                                           

  Service           Successfully      Demonstrates    Can perform      Struggles to
  Management Skills starts, stops,    proficiency in  basic service    perform even basic
                    restarts, and     managing        management       service management
                    configures        services, but   tasks, but may   tasks.
                    services using    may encounter   need assistance  
                    the Services app. minor           or guidance.     
                                      difficulties.                    

  Custom Service    Successfully      Can create a    Has limited      Cannot create a
  Creation          creates and       custom service, experience with  custom service.
                    manages a custom  but may         creating custom  
                    service using the encounter minor services.        
                    appropriate tools difficulties or                  
                    and techniques.   require                          
                                      assistance.                      

  Problem-Solving   Demonstrates      Can effectively May require      Struggles to
                    strong            troubleshoot    assistance to    troubleshoot and
                    problem-solving   and resolve     troubleshoot     resolve issues.
                    skills when       most issues     some issues.     
                    encountering      related to                       
                    challenges or     service                          
                    errors.           management.                      

  Documentation and Provides clear    Documents the   Provides basic   Does not provide
  Reporting         and concise       lab activities  documentation,   any documentation
                    documentation of  adequately, but but may be       or reporting.
                    the lab           may lack some   disorganized or  
                    activities,       detail or       incomplete.      
                    including         clarity.                         
                    relevant                                           
                    screenshots and                                    
                    observations.                                      

  **Score:**        **/50**                                            
  ---------------------------------------------------------------------------------------
