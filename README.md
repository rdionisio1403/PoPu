# ***PoPu*** (***P***ressure ***O***ver & ***P***ressure ***U***nder) Dataset

## A pressure map dataset with data from two different sensor sheets, one placed over a mattress and another placed under it.

Contains pressure maps from ***60 participants*** in ***28 different predetermined poses***.
For each pose volunteers were asked to slightly shift their bodies twice.
The data gathering process resulted in 30 samples per pose, which amounts to ***50400 samples***.

The data files are divided throughout folders that contain the data for each of the volunteers.

The structure of each of the files that contain the pressure data is as follows:

```
{
  volunteer_id: <identifier for volunteer>,
  sex: <sex of volunteer>,
  height: <height of volunteer in cm>,
  weight: <weight of volunteer in kg>,
  tactilus_columns: 27,
  tactilus_rows: 64,
  sensomatt_columns: 6,
  sensomatt_rows: 12,
  position: <position of volunteer>,
  variation: <variation number>,
  snapshots: {
    <snapshot number_0>: {
        id: <identifier generated for specific sample>,
        tactilus_readings: [<list of values from top sensor sheet>,
        sensomatt_readings: [<list of values from bottom sensor sheet>]
    <snapshot number_n>: {
        id: <identifier generated for specific sample>,
        tactilus_readings: [<list of values from top sensor sheet>,
        sensomatt_readings: [<list of values from bottom sensor sheet>]
}
```

This dataset can be used for posture classification studies, sleep disorder studies, fall prevention studies, among others...

The addition of a data layer that represents pressure data from below the mattress can solve issues related to health concerns, like skin contact with odd materials from the sensor sheets.
