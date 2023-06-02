# ***PoPu*** (***P***ressure ***O***ver & ***P***ressure ***U***nder) Dataset

## A pressure map dataset with data from two different sensor sheets, one placed over a mattress and another placed under it.

Contains pressure maps from ***60 participants*** in ***28 different predetermined poses***.
For each pose volunteers were asked to slightly shift their body twice.
The data gathering process resulted in 30 samples per pose, divided when the subject was asked to shift their position slightly, which results in a total of ***50400 samples***.

The data files are divided throughout folders that contain the data for each of the volunteers.
The three different layers of data (pressure over, pressure under and segmentation) are in different folders, with the following structure:
```
.
└── PoPu_data/
    ├── sensomatt_data/
    │   ├── 1(volunteer_id)/
    │   │   └── <position+variation_json_data_files_with_bottom_pressure_data>
    │   ├── (...)
    │   └── 60(volunteer_id)/
    │       └── <position+variation_json_data_files_with_bottom_pressure_data>
    ├── tactilus_data/
    │   ├── 1(volunteer_id)/
    │   │   └── <position+variation_json_data_files_with_top_pressure_data>
    │   ├── (...)
    │   └── 60(volunteer_id)/
    │       └── <position+variation_json_data_files_with_top_pressure_data>
    └── segmentation_data/
        ├── 1(volunteer_id)/
        │   ├── <position+variation_json_files_with_segmentation_results>
        │   └── <segment_images_folder>/
        │       └── <position+variation_segment_image>
        ├── (...)
        └── 60(volunteer_id)/
            ├── <position+variation_json_files_with_segmentation_results>
            └── <segment_images_folder>/
                └── <position+variation_segment_image>
```
The structure of each of the files that contain the pressure data is as follows:

```
{
  volunteer_id: <identifier_for_volunteer>,
  sex: <sex_of_volunteer>,
  height: <height_of_volunteer_in_cm>,
  weight: <weight_of_volunteer_in kg>,
  <sensor_sheet name>_columns: <number_of_columns>,
  <sensor_sheet name>_rows: <number_of_rows>,
  position: <position_of_volunteer>,
  variation: <variation_number>,
  snapshots: {
    0: {
      id: <identifier_generated_for_specific_sample>,
      <sensor_sheet_name>_readings: [<list_of_values_from_sensor_sheet>,
    }
  <snapshot_number_n>: {
      id: <identifier_generated_for_specific_sample>,
      <sensor_sheet_name>_readings: [<list_of_values_from_sensor_sheet>
  }
}

```

The structure of the segmentation files that contain the segments generated is as follows:

```
{
  id: <image_name>,
  annotations: [
    {
      id: <body_part_number_in_image>,
      completed_by: 1,
      result: 
        [<list_of_polygons_found_in_image>
          {
              original_width: <image_width>,
              original_height: <image_height>,
              image_rotation: <image_rotation>,
              value: { 
                  points: [ <list_of_polygon_vertices_(ordered_clockwise)>
                      [<x>,<y>],
                      (...)
                      [<x>,<y>]
                  ],
                  closed: <true_if_polygon_closed_false_otherwise>,
                  polygonlabels: [<name_of_body_part>]
              },
              id: <randomly_generated_id>,
              from_name: "label",
              to_name: "image",
              type: "polygonlabels",
              origin: "manual"
          },
          (...rest_of_polygons…)
        ],
        <info_regarding_segmentation_process_(omitted)>
    }
  ],
  file_upload: <segmentation_image_name>,
  <info_regarding_image_(omitted)>
}

```

This dataset can be used for posture classification studies, sleep disorder studies, fall prevention studies, among others...

The addition of a data layer that represents pressure data from below the mattress can solve issues related to health concerns, like skin contact with odd materials from the sensor sheets.
