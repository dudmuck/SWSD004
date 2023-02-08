# build Semtech reference tracker firmware with STM32CubeIDE
## Build instructions
- Use [STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html)
- From in the STM32CubeIDE:
  - File → Import → under **General** category, select **Existing Projects into workspace** → next
  - Check **Select root directory**
  - Click on browse, Navigate to directory ``apps/demonstrations/tracker_application/STM32CubeIDE``
  - Select folder there, the ``STM32CubeIDE`` directory
  - Back in the import dialog, in the import section, you’ll see the project name
  - Click on finish
  - The project will now be in your STM32CubeIDE workspace, and can be built
- Changing region (two steps, change #define and enable region source file)
  - Adjust preprocessor directives
    - Highlight tracker_application  project in Project Explorer
    - Right click → properties, or from menu Project → properties
    - Under C / C++ Build → settings
    - Comment out the enabled region by adding an underscore, effectively commenting it out
    - Remove the underscore from your desired region (uncommenting it)
    - Apply and Close this properties dialog
  - Back in the Project Explorer
    - In the tracker_application project, under src → lora_basics_modem → regions, right click on the enabled region source file → resource configurations → Exclude from build.  In the dialog, Select All to disable building of this region sources file.
   - Repeat the same process for your desired region to enable building of the desired region source file.
- enable debugging:
  - if you only wish to run (program flash), you can "Run As" in stm32CubeIDE.
  - to debug, open in your editor the file ``smtc_hal/inc/smtc_hal_options.h``
  - define ``HAL_LOW_POWER_MODE`` as ``HAL_FEATURE_OFF``
  - define ``HAL_HW_DEBUG_PROBE`` as ``HAL_FEATURE_ON``
  - st-link debugger will now function continuously on the tracker
  - to restore low-power operation after finished debugging, restore to the original values ``HAL_LOW_POWER_MODE`` and ``HAL_HW_DEBUG_PROBE`` in ``smtc_hal_options.h``

