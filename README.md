you need to download the CSV into your config folder first, then reference it locally.

Get the raw file and save it as partitions32mb.csv next to your YAML (usually under /homeassistant/esphome/):
```
esp32:
  board: esp32-s3-devkitc-1-n32r8v
  flash_size: 32MB
  partitions: partitions32mb.csv
  framework:
    type: esp-idf
    sdkconfig_options:
      CONFIG_SPIRAM: "y"
      CONFIG_ESP32S3_SPIRAM_SUPPORT: "y"
      CONFIG_SPIRAM_FETCH_INSTRUCTIONS: "y"
      CONFIG_SPIRAM_RODATA: "y"
      CONFIG_SPIRAM_MALLOC_RESERVE_INTERNAL: "65536"
      CONFIG_MBEDTLS_EXTERNAL_MEM_ALLOC: "y"
      CONFIG_SPIRAM_USE_CAPS_ALLOC: "n"
      CONFIG_SPIRAM_USE_MALLOC: "y"
      CONFIG_SPIRAM_MALLOC_ALWAYSINTERNAL: "4096"
      CONFIG_SPIRAM_TRY_ALLOCATE_WIFI_LWIP: "y"
      CONFIG_MDNS_TASK_CREATE_FROM_SPIRAM: "y"
      CONFIG_MDNS_MEMORY_ALLOC_SPIRAM: "y"
    advanced:
      enable_idf_experimental_features: true # required for 32MB flash

```
