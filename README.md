
# OTAI Exention to SAI

## Instruction
Extend all OTAI objects to SAI by the following command:

    python3 extension.py

Make metadata for the extension SAI by the following commands:

    sudo apt-get install doxygen perl
    cd SAI/meta
    make

After the code compiles successfully, the html manual and meta data code would be automatically generated, also the .o object files would be there too.
You can open the manual of html/index.html by double clicking the mouse or type the following command:

    firefox html/index.html

Just take a quick look at OTAI manual (eg. attenuator) by the following command:

    firefox html/group__SAIEXPERIMENTALOTAIATTENUATOR.html

<img src="https://github.com/oplklum/Images/blob/master/otai-atten.png?raw=true">

You'll see the new created files of saimetadata.h and saimetadata.c. Some OTAI object examples are shown below:

    const sai_api_extensions_t sai_metadata_sai_api_extensions_t_enum_values[] = {
        SAI_API_BMTOR,
        SAI_API_OTAI_ATTENUATOR,
        SAI_API_OTAI_OA,
        SAI_API_OTAI_OCM,
        SAI_API_OTAI_OSC,
        SAI_API_OTAI_OTDR,
        -1
    };

    const sai_object_type_extensions_t sai_metadata_sai_object_type_extensions_t_enum_values[] = {
        SAI_OBJECT_TYPE_TABLE_BITMAP_CLASSIFICATION_ENTRY,
        SAI_OBJECT_TYPE_TABLE_BITMAP_ROUTER_ENTRY,
        SAI_OBJECT_TYPE_TABLE_META_TUNNEL_ENTRY,
        SAI_OBJECT_TYPE_OTAI_ATTENUATOR,
        SAI_OBJECT_TYPE_OTAI_OA,
        SAI_OBJECT_TYPE_OTAI_OCM,
        SAI_OBJECT_TYPE_OTAI_OSC,
        SAI_OBJECT_TYPE_OTAI_OTDR,
        -1
    };

    const sai_enum_metadata_t sai_metadata_enum_sai_otai_attenuator_attr_t = {
        .name              = "sai_otai_attenuator_attr_t",
        .valuescount       = 8,
        .values            = (const int*)sai_metadata_sai_otai_attenuator_attr_t_enum_values,
        .valuesnames       = sai_metadata_sai_otai_attenuator_attr_t_enum_values_names,
        .valuesshortnames  = sai_metadata_sai_otai_attenuator_attr_t_enum_values_short_names,
        .containsflags     = false,
        .flagstype         = SAI_ENUM_FLAGS_TYPE_NONE,
        .ignorevalues      = NULL,
        .ignorevaluesnames = NULL,
        .objecttype        = (sai_object_type_t)SAI_OBJECT_TYPE_OTAI_ATTENUATOR,
    };

    const sai_otai_attenuator_stat_t sai_metadata_sai_otai_attenuator_stat_t_enum_values[] = {
        SAI_OTAI_ATTENUATOR_STAT_ACTUAL_ATTENUATION,
        SAI_OTAI_ATTENUATOR_STAT_OUTPUT_POWER_TOTAL,
        SAI_OTAI_ATTENUATOR_STAT_OPTICAL_RETURN_LOSS,
        -1
    };

## Note
- For this prototype, OTAI only contains OA, OCM, ATTENUATOR and OTDR. However, this mechanism is generic. To cover other OTAI objects and APIs, simply add other OTAI header files into OTAI submodule.
- These steps can be automatized and integrated into ``sonic-sairedis`` build process.

