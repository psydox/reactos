PROJECT(SHELL)

if(DBG)
    add_definitions(-D_DEBUG=1) # CORE-17505
endif()

list(APPEND SOURCE
    appbar.cpp
    desktop.cpp
    explorer.cpp
    notifyiconscust.cpp
    rshell.cpp
    settings.cpp
    shellservice.cpp
    startctxmnu.cpp
    startmnu.cpp
    startmnucust.cpp
    startmnusite.cpp
    startup.cpp
    syspager.cpp
    taskband.cpp
    taskswnd.cpp
    tbsite.cpp
    trayclock.cpp
    traydeskbtn.cpp
    trayntfy.cpp
    trayprop.cpp
    traywnd.cpp
    util.cpp
    precomp.h)

file(GLOB explorer_rc_deps res/*.*)
add_rc_deps(explorer.rc ${explorer_rc_deps})
add_executable(explorer ${SOURCE} explorer.rc)
target_link_libraries(explorer uuid wine cpprt atl_classes)
set_module_type(explorer win32gui UNICODE)
add_importlibs(explorer advapi32 gdi32 user32 comctl32 ole32 oleaut32 shell32 browseui shlwapi shdocvw version uxtheme msvcrt kernel32 ntdll)
add_pch(explorer precomp.h SOURCE)
add_cd_file(TARGET explorer DESTINATION reactos FOR all)
