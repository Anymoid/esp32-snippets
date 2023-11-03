cmake_minimum_required(VERSION 3.5)
include($ENV{IDF_PATH}/tools/cmake/project.cmake)

# Set a variable to represent the directory
set(c cpp_utils)

# I might be missing the SRCS and PRIV_REQUIRES args
idf_component_register(
    INCLUDE_DIRS "${c}"
    REQUIRES nkolban # Adjust this to the actual requirements of your component.
)

# Conditional source file compilation based on CONFIG_NKOLBAN
if(CONFIG_NKOLBAN)
    target_sources(${COMPONENT_LIB} PRIVATE
        "${c}/Task.cpp"
        "${c}/FreeRTOS.cpp"
        "${c}/GeneralUtils.cpp"
    )
endif()

# Conditional source file compilation based on CONFIG_NKOLBAN_BLE
if(CONFIG_NKOLBAN_BLE)
    target_sources(${COMPONENT_LIB} PRIVATE
        "${c}/BLEAddress.cpp"
        "${c}/BLEAdvertisedDevice.cpp"
        "${c}/BLEAdvertising.cpp"
        "${c}/BLECharacteristic.cpp"
        "${c}/BLECharacteristicCallbacks.cpp"
        "${c}/BLECharacteristicMap.cpp"
        "${c}/BLEClient.cpp"
        "${c}/BLEDescriptor.cpp"
        "${c}/BLEDescriptorMap.cpp"
        "${c}/BLEDevice.cpp"
        "${c}/BLERemoteCharacteristic.cpp"
        "${c}/BLERemoteDescriptor.cpp"
        "${c}/BLERemoteService.cpp"
        "${c}/BLEScan.cpp"
        "${c}/BLEServer.cpp"
        "${c}/BLEService.cpp"
        "${c}/BLEServiceMap.cpp"
        "${c}/BLEUUID.cpp"
        "${c}/BLEUtils.cpp"
        "${c}/BLEValue.cpp"
    )
endif()

# Conditional source file compilation based on CONFIG_NKOLBAN_BLE2902
if(CONFIG_NKOLBAN_BLE2902)
    target_sources(${COMPONENT_LIB} PRIVATE "${c}/BLE2902.cpp")
endif()
