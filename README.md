# astrotime


NOAA astrological algorithms for sunrise and sunset ported to Go

## Conveniance Functions

- `func CalcSunrise(t time.Time, latitude float64, longitude float64) time.Time` calculates the sunrise, in local time, on the day t at the location specified in longitude and latitude.
- `func NextSunrise(tAfter time.Time, latitude float64, longitude float64) (tSunrise time.Time)` returns date/time of the next sunrise after tAfter
- `func CalcSunset(t time.Time, latitude float64, longitude float64) time.Time` calculates the sunset, in local time,  on the day t at the location specified in longitude and latitude.
- `func NextSunset(tAfter time.Time, latitude float64, longitude float64) (tSunset time.Time)` returns date/time of the next sunset after tAfter

## Core Functions

- `func CalcDawn(t time.Time, latitude float64, longitude float64, solarElevation float64) time.Time` calculates Dawn or Sunrise (depending on solarElevation given), in local time, on the day t at the location specified in longitude and latitude.
- `func CalcDusk(t time.Time, latitude float64, longitude float64, solarElevation float64) time.Time` calculates Dusk or Sunset (depending on solarElevation given), in local time, on the day t at the location specified in longitude and latitude.
- `func NextDawn(tAfter time.Time, latitude float64, longitude float64, solarElevation float64) (tSunrise time.Time)` returns date/time of
the specified solarElevation before Sunrise after tAfter
- `func NextDusk(tAfter time.Time, latitude float64, longitude float64, solarElevation float64) (tSunrise time.Time)` returns date/time of the specified solarElevation after Sunset after tAfter.

## Predefined Solar Elevations

- `ASTRONOMICAL_DAWN`
- `ASTRONOMICAL_DUSK´
- `NAUTICAL_DAWN`
- `NAUTICAL_DUSK`
- `CIVIL_DAWN`
- `CIVIL_DUSK`
- `SUNRISE`
- `SUNSET`
- `GOLDEN_HOUR`


## Install

``` sh
go get -u github.com/btittelbach/astrotime
```

## Example

```go
package main

import (
        "astrotime"
        "fmt"
        "time"
)

const LATITUDE = float64(38.8895)
const LONGITUDE = float64(77.0352)

func main() {
        t := astrotime.NextSunrise(time.Now(), LATITUDE, LONGITUDE)

        tzname, _ := t.Zone()
        fmt.Printf("The next sunrise at the Washington Monument is %d:%02d %s on %d/%d/%d.\n", t.Hour(), t.Minute(), tzname, t.Month(), t.Day(), t.Year())
}
```
