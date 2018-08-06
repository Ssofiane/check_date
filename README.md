#!/usr/bin/env bash

while IFS=";/" read start_day start_month start_year start_time group end_day end_month end_year end_time; do
    start_epoch=$(date -d "$start_month/$start_day/$start_year $start_time" +%s)
    end_epoch=$(date -d "$end_month/$end_day/$end_year $end_time" +%s)
    diff=$((end_epoch - start_epoch))
    echo "$start_day/$start_month/$start_year $start_time|$end_day/$end_month/$end_year $end_time|$start_epoch|$end_epoch|$diff"
done < /dev/stdin
