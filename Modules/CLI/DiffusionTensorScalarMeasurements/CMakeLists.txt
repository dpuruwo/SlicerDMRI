
#-----------------------------------------------------------------------------
set(MODULE_NAME DiffusionTensorScalarMeasurements)

#-----------------------------------------------------------------------------

#
# SlicerExecutionModel
#
find_package(SlicerExecutionModel REQUIRED)
include(${SlicerExecutionModel_USE_FILE})

#-----------------------------------------------------------------------------
set(${MODULE_NAME}_TARGET_LIBRARIES
  MRMLCore vtkTeem vtkDMRI ${VTK_LIBRARIES}
  )

#-----------------------------------------------------------------------------
SEMMacroBuildCLI(
  NAME ${MODULE_NAME}
  LOGO_HEADER ${Slicer_ACTUAL_SOURCE_DIR}/Resources/ITKLogo.h
  TARGET_LIBRARIES ${${MODULE_NAME}_TARGET_LIBRARIES}
  INCLUDE_DIRECTORIES
    ${vtkDMRI_INCLUDE_DIRS}
    ${vtkTeem_INCLUDE_DIRS}
    ${MRMLCore_INCLUDE_DIRS}
    ${VTK_INCLUDE_DIRS}
  EXECUTABLE_ONLY
  )

#-----------------------------------------------------------------------------
if(BUILD_TESTING)
  add_subdirectory(Testing)
endif()
