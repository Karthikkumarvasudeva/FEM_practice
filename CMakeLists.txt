
##
#Cmake Script
##

#Set the name of the project and target:
SET(TARGET "main")

# DEclare all the source files the target consists of:
SET (TARGET_SRC
   ${TARGET}.cc
   # You can specify additional files here!
   )

# Usuually, you will not need ot modify anything beyound this ENTRY_POINT
CMAKE_MINIMUM_REQUIRED(VERSION 2.8.8)

FIND_PACKAGE(deal.II 8.0 QUIET
   HINTS ${deal.II_DIR} ${DEAL_II_DIR} ../ ../ ../ $ENV{DEAL_II_DIR}
   )
IF(NOT ${deal.II_FOUND})
  MESSAGE(FATAL_ERROR "\n"
    "*** could not locate deal.II. ***\n\n"
    "you may want to either pass a flag -DDEAL_II_DIR=/path/to/deal.II to cmake\n"
    "or set an environment variable \"DEAL_II_DIR\" that contains this path."
)
ENDIF()

DEAL_II_INITIALIZE_CACHED_VARIABLES()
PROJECT(${TARGET})
DEAL_II_INVOKE_AUTOPILOT()
