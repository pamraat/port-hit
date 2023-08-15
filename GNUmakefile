# NGA location if not yet defined
NGA_HOME ?= <Enter the path to NGA2 directory>

# Compilation parameters
PRECISION = DOUBLE
USE_MPI   = TRUE
USE_FFTW  = TRUE
USE_HYPRE = TRUE
USE_LAPACK= TRUE
PROFILE   = FALSE
DEBUG     = FALSE
COMP      = gnu
EXEBASE   = nga

# Directories that contain user-defined code
Udirs   := src

# Include user-defined sources
Upack   += $(foreach dir, $(Udirs), $(wildcard $(dir)/Make.package))
Ulocs   += $(foreach dir, $(Udirs), $(wildcard $(dir)))
include $(Upack)
INCLUDE_LOCATIONS += $(Ulocs)
VPATH_LOCATIONS   += $(Ulocs)

# External libraries are defined in .profile/.bashrc/.zshrc, but could be defined here as well
HYPRE_DIR = <Enter the path to hypre directory>
IRL_DIR   = <Enter the path to IRL directory>
LAPACK_DIR = <Enter the path to lapack directory>
FFTW_DIR = <Enter the path to FFTW directory>

# NGA compilation definitions
include $(NGA_HOME)/tools/GNUMake/Make.defs

# Include NGA base code
Bdirs   := particles core constant_density data solver config grid libraries
Bpack   += $(foreach dir, $(Bdirs), $(NGA_HOME)/src/$(dir)/Make.package)
include $(Bpack)

# Inform user of Make.packages used
ifdef Ulocs
   $(info Taking user code from: $(Ulocs))
endif
$(info Taking base code from: $(Bdirs))

# Target definition
all: $(executable)
	@echo COMPILATION SUCCESSFUL

# NGA compilation rules
include $(NGA_HOME)/tools/GNUMake/Make.rules
