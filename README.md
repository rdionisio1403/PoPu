# ***PoPu*** (***P***ressure ***O***ver & ***P***ressure ***U***nder) Dataset

## A pressure map dataset with data from two different sensor sheets, one placed over a mattress and another placed under it.

Contains pressure maps from ***60 participants*** in ***28 different predetermined poses***.
For each pose volunteers were asked to slightly shift their body twice.
The data gathering process resulted in 30 samples per pose, divided when the subject was asked to shift their position slightly, which results in a total of ***50400 samples***.

The data files are divided throughout folders that contain the data for each of the volunteers.

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

This dataset can be used for posture classification studies, sleep disorder studies, fall prevention studies, among others...

The addition of a data layer that represents pressure data from below the mattress can solve issues related to health concerns, like skin contact with odd materials from the sensor sheets.
