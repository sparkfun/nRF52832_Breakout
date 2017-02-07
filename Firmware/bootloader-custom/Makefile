PROJECT_NAME := dfu_dual_bank_serial_s132_pca10040

# Replace SDK_PATH with the relative path to your Nordic nRF5 SDK (v11.0.0):
SDK_PATH = ../../../../../../../../Nordic
# Folders below "Nordic" include "components", "examples", etc.

# PROJ_DIR includes main.c, and the "config" folder:
PROJ_DIR := .

export OUTPUT_FILENAME
MAKEFILE_NAME := $(MAKEFILE_LIST)
MAKEFILE_DIR := $(dir $(MAKEFILE_NAME) ) 

TEMPLATE_PATH = $(SDK_PATH)/components/toolchain/gcc
ifeq ($(OS),Windows_NT)
include $(TEMPLATE_PATH)/Makefile.windows
else
include $(TEMPLATE_PATH)/Makefile.posix
endif

MK := mkdir
RM := rm -rf

#echo suspend
ifeq ("$(VERBOSE)","1")
NO_ECHO := 
else
NO_ECHO := @
endif

# Toolchain commands
CC              := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-gcc'
AS              := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-as'
AR              := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-ar' -r
LD              := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-ld'
NM              := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-nm'
OBJDUMP         := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-objdump'
OBJCOPY         := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-objcopy'
SIZE            := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-size'

#function for removing duplicates in a list
remduplicates = $(strip $(if $1,$(firstword $1) $(call remduplicates,$(filter-out $(firstword $1),$1))))

#source common to all targets
C_SOURCE_FILES += \
	$(SDK_PATH)/components/libraries/util/app_error.c \
	$(SDK_PATH)/components/libraries/util/app_error_weak.c \
	$(SDK_PATH)/components/libraries/scheduler/app_scheduler.c \
	$(SDK_PATH)/components/libraries/timer/app_timer.c \
	$(SDK_PATH)/components/libraries/timer/app_timer_appsh.c \
	$(SDK_PATH)/components/libraries/util/app_util_platform.c \
	$(SDK_PATH)/components/libraries/bootloader_dfu/bootloader.c \
	$(SDK_PATH)/components/libraries/bootloader_dfu/bootloader_settings.c \
	$(SDK_PATH)/components/libraries/bootloader_dfu/bootloader_util.c \
	$(SDK_PATH)/components/libraries/crc16/crc16.c \
	$(SDK_PATH)/components/libraries/bootloader_dfu/dfu_dual_bank.c \
	$(SDK_PATH)/components/libraries/bootloader_dfu/dfu_init_template.c \
	$(SDK_PATH)/components/libraries/bootloader_dfu/dfu_transport_serial.c \
	$(SDK_PATH)/components/libraries/hci/hci_mem_pool.c \
	$(SDK_PATH)/components/libraries/hci/hci_slip.c \
	$(SDK_PATH)/components/libraries/hci/hci_transport.c \
	$(SDK_PATH)/components/libraries/util/nrf_assert.c \
	$(SDK_PATH)/components/libraries/uart/app_uart.c \
	$(SDK_PATH)/components/drivers_nrf/delay/nrf_delay.c \
	$(SDK_PATH)/components/drivers_nrf/common/nrf_drv_common.c \
	$(SDK_PATH)/components/drivers_nrf/uart/nrf_drv_uart.c \
	$(SDK_PATH)/components/drivers_nrf/pstorage/pstorage_raw.c \
	$(PROJ_DIR)/main.c \
	$(SDK_PATH)/components/ble/common/ble_advdata.c \
	$(SDK_PATH)/components/ble/common/ble_conn_params.c \
	$(SDK_PATH)/components/ble/common/ble_srv_common.c \
	$(SDK_PATH)/components/toolchain/system_nrf52.c \
	$(SDK_PATH)/components/softdevice/common/softdevice_handler/softdevice_handler.c \
	$(SDK_PATH)/components/softdevice/common/softdevice_handler/softdevice_handler_appsh.c \
	$(SDK_PATH)/components/libraries/simple_timer/app_simple_timer.c \
	$(SDK_PATH)/components/drivers_nrf/timer/nrf_drv_timer.c \

#assembly files common to all targets
ASM_SOURCE_FILES  = $(SDK_PATH)/components/toolchain/gcc/gcc_startup_nrf52.s

#includes common to all targets
INC_PATHS += \
	-I $(PROJ_DIR)/config/dfu_dual_bank_serial_s132_pca10040 \
	-I $(PROJ_DIR)/config \
	-I $(SDK_PATH)/components/libraries/bootloader_dfu/hci_transport \
	-I $(SDK_PATH)/components/libraries/bootloader_dfu \
	-I $(SDK_PATH)/components/libraries/scheduler \
	-I $(SDK_PATH)/components/drivers_nrf/config \
	-I $(SDK_PATH)/examples/bsp \
	-I $(SDK_PATH)/components/drivers_nrf/delay \
	-I $(SDK_PATH)/components/libraries/crc16 \
	-I $(SDK_PATH)/components/softdevice/s132/headers/nrf52 \
	-I $(SDK_PATH)/components/libraries/util \
	-I $(SDK_PATH)/components/drivers_nrf/pstorage \
	-I $(SDK_PATH)/components/drivers_nrf/uart \
	-I $(SDK_PATH)/components/ble/common \
	-I $(SDK_PATH)/components/libraries/hci/config \
	-I $(SDK_PATH)/components/libraries/uart \
	-I $(SDK_PATH)/components/device \
	-I $(SDK_PATH)/components/libraries/hci \
	-I $(SDK_PATH)/components/libraries/timer \
	-I $(SDK_PATH)/components/softdevice/s132/headers \
	-I $(SDK_PATH)/components/toolchain/CMSIS/Include \
	-I $(SDK_PATH)/components/drivers_nrf/hal \
	-I $(SDK_PATH)/components/toolchain/gcc \
	-I $(SDK_PATH)/components/toolchain \
	-I $(SDK_PATH)/components/drivers_nrf/common \
	-I $(SDK_PATH)/components/softdevice/common/softdevice_handler \
	-I $(SDK_PATH)/components/libraries/simple_timer \
	-I $(SDK_PATH)/components/drivers_nrf/timer \

OBJECT_DIRECTORY = _build
LISTING_DIRECTORY = $(OBJECT_DIRECTORY)
OUTPUT_BINARY_DIRECTORY = $(OBJECT_DIRECTORY)

# Sorting removes duplicates
BUILD_DIRECTORIES := $(sort $(OBJECT_DIRECTORY) $(OUTPUT_BINARY_DIRECTORY) $(LISTING_DIRECTORY) )

#flags common to all targets
CFLAGS  = -DNRF52
#CFLAGS += -DBOARD_PCA10040
CFLAGS += -DBOARD_CUSTOM
CFLAGS += -DNRF52_PAN_12
CFLAGS += -DNRF52_PAN_15
CFLAGS += -DNRF52_PAN_58
CFLAGS += -DNRF52_PAN_55
CFLAGS += -DNRF52_PAN_54
CFLAGS += -DNRF52_PAN_31
CFLAGS += -DNRF52_PAN_30
CFLAGS += -DNRF52_PAN_51
CFLAGS += -DNRF52_PAN_36
CFLAGS += -DNRF52_PAN_53
CFLAGS += -D__HEAP_SIZE=0
CFLAGS += -DS132
CFLAGS += -DCONFIG_GPIO_AS_PINRESET
CFLAGS += -DBLE_STACK_SUPPORT_REQD
CFLAGS += -DBSP_DEFINES_ONLY
CFLAGS += -DSWI_DISABLE0
CFLAGS += -DNRF52_PAN_20
CFLAGS += -DNRF52_PAN_64
CFLAGS += -DSOFTDEVICE_PRESENT
CFLAGS += -DNRF52_PAN_62
CFLAGS += -DNRF52_PAN_63
CFLAGS += -mcpu=cortex-m4
CFLAGS += -mthumb -mabi=aapcs --std=gnu99
CFLAGS += -Wall -Werror -Os -g3
CFLAGS += -mfloat-abi=hard -mfpu=fpv4-sp-d16
# keep every function in separate section. This will allow linker to dump unused functions
CFLAGS += -ffunction-sections -fdata-sections -fno-strict-aliasing
CFLAGS += -fno-builtin --short-enums 
# keep every function in separate section. This will allow linker to dump unused functions
LDFLAGS += -Xlinker -Map=$(LISTING_DIRECTORY)/$(OUTPUT_FILENAME).map
LDFLAGS += -mthumb -mabi=aapcs -L $(TEMPLATE_PATH) -T$(LINKER_SCRIPT)
LDFLAGS += -mcpu=cortex-m4
LDFLAGS += -mfloat-abi=hard -mfpu=fpv4-sp-d16
# let linker to dump unused sections
LDFLAGS += -Wl,--gc-sections
# use newlib in nano version
LDFLAGS += --specs=nano.specs -lc -lnosys

# Assembler flags
ASMFLAGS += -x assembler-with-cpp
ASMFLAGS += -DNRF52
ASMFLAGS += -DBOARD_PCA10040
ASMFLAGS += -DNRF52_PAN_12
ASMFLAGS += -DNRF52_PAN_15
ASMFLAGS += -DNRF52_PAN_58
ASMFLAGS += -DNRF52_PAN_55
ASMFLAGS += -DNRF52_PAN_54
ASMFLAGS += -DNRF52_PAN_31
ASMFLAGS += -DNRF52_PAN_30
ASMFLAGS += -DNRF52_PAN_51
ASMFLAGS += -DNRF52_PAN_36
ASMFLAGS += -DNRF52_PAN_53
ASMFLAGS += -D__HEAP_SIZE=0
ASMFLAGS += -DS132
ASMFLAGS += -DCONFIG_GPIO_AS_PINRESET
ASMFLAGS += -DBLE_STACK_SUPPORT_REQD
ASMFLAGS += -DBSP_DEFINES_ONLY
ASMFLAGS += -DSWI_DISABLE0
ASMFLAGS += -DNRF52_PAN_20
ASMFLAGS += -DNRF52_PAN_64
ASMFLAGS += -DSOFTDEVICE_PRESENT
ASMFLAGS += -DNRF52_PAN_62
ASMFLAGS += -DNRF52_PAN_63

#default target - first one defined
default: clean sfe_nrf52832_dfu

#building all targets
all: clean
	$(NO_ECHO)$(MAKE) -f $(MAKEFILE_NAME) -C $(MAKEFILE_DIR) -e cleanobj
	$(NO_ECHO)$(MAKE) -f $(MAKEFILE_NAME) -C $(MAKEFILE_DIR) -e sfe_nrf52832_dfu

#target for printing all targets
help:
	@echo following targets are available:
	@echo 	sfe_nrf52832_dfu

C_SOURCE_FILE_NAMES = $(notdir $(C_SOURCE_FILES))
C_PATHS = $(call remduplicates, $(dir $(C_SOURCE_FILES) ) )
C_OBJECTS = $(addprefix $(OBJECT_DIRECTORY)/, $(C_SOURCE_FILE_NAMES:.c=.o) )

ASM_SOURCE_FILE_NAMES = $(notdir $(ASM_SOURCE_FILES))
ASM_PATHS = $(call remduplicates, $(dir $(ASM_SOURCE_FILES) ))
ASM_OBJECTS = $(addprefix $(OBJECT_DIRECTORY)/, $(ASM_SOURCE_FILE_NAMES:.s=.o) )

vpath %.c $(C_PATHS)
vpath %.s $(ASM_PATHS)

OBJECTS = $(C_OBJECTS) $(ASM_OBJECTS)

sfe_nrf52832_dfu: OUTPUT_FILENAME := sfe_nrf52832_dfu
sfe_nrf52832_dfu: LINKER_SCRIPT = dfu_gcc_nrf52.ld

sfe_nrf52832_dfu: $(BUILD_DIRECTORIES) $(OBJECTS)
	@echo Linking target: $(OUTPUT_FILENAME).out
	$(NO_ECHO)$(CC) $(LDFLAGS) $(OBJECTS) $(LIBS) -lm -o $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out
	$(NO_ECHO)$(MAKE) -f $(MAKEFILE_NAME) -C $(MAKEFILE_DIR) -e finalize

## Create build directories
$(BUILD_DIRECTORIES):
	echo $(MAKEFILE_NAME)
	$(MK) $@

# Create objects from C SRC files
$(OBJECT_DIRECTORY)/%.o: %.c
	@echo Compiling file: $(notdir $<)
	$(NO_ECHO)$(CC) $(CFLAGS) $(INC_PATHS) -c -o $@ $<

# Assemble files
$(OBJECT_DIRECTORY)/%.o: %.s
	@echo Assembly file: $(notdir $<)
	$(NO_ECHO)$(CC) $(ASMFLAGS) $(INC_PATHS) -c -o $@ $<
# Link
$(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out: $(BUILD_DIRECTORIES) $(OBJECTS)
	@echo Linking target: $(OUTPUT_FILENAME).out
	$(NO_ECHO)$(CC) $(LDFLAGS) $(OBJECTS) $(LIBS) -lm -o $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out
## Create binary .bin file from the .out file
$(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).bin: $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out
	@echo Preparing: $(OUTPUT_FILENAME).bin
	$(NO_ECHO)$(OBJCOPY) -O binary $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).bin

## Create binary .hex file from the .out file
$(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).hex: $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out
	@echo Preparing: $(OUTPUT_FILENAME).hex
	$(NO_ECHO)$(OBJCOPY) -O ihex $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).hex

finalize: genbin genhex echosize

genbin:
	@echo Preparing: $(OUTPUT_FILENAME).bin
	$(NO_ECHO)$(OBJCOPY) -O binary $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).bin

## Create binary .hex file from the .out file
genhex: 
	@echo Preparing: $(OUTPUT_FILENAME).hex
	$(NO_ECHO)$(OBJCOPY) -O ihex $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).hex
echosize:
	-@echo ''
	$(NO_ECHO)$(SIZE) $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out
	-@echo ''

clean:
	$(RM) $(BUILD_DIRECTORIES)

cleanobj:
	$(RM) $(BUILD_DIRECTORIES)/*.o
	
flash: sfe_nrf52832_dfu
	@echo Flashing: $(OUTPUT_BINARY_DIRECTORY)/$<.hex
	nrfjprog --program $(OUTPUT_BINARY_DIRECTORY)/$<.hex -f nrf52  --chiperase
	nrfjprog --reset -f nrf52

flash_softdevice: sfe_nrf52832_dfu
	@echo Flashing: s132_nrf52_2.0.0_softdevice.hex
	nrfjprog --program ../../../../../../../../Nordic/components/softdevice/s132/hex/s132_nrf52_2.0.0_softdevice.hex -f nrf52 --chiperase
	@echo Flashing: $(OUTPUT_BINARY_DIRECTORY)/$<.hex
	nrfjprog --program $(OUTPUT_BINARY_DIRECTORY)/$<.hex -f nrf52
	nrfjprog --reset -f nrf52
## Flash softdevice