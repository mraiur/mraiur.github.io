---
published: false
title: javascript matching date or duration
layout: post
tags: []
categories: [none]
---
```
Ext.define('OST.utils.VTypes', {
    singleton: true,

    create: function(){
        var dateDurationRegex = /^(([0-9]{1,2}(|(,[0-9]{1,9}|:[0-9]{1,2})))|((1[0-2]|0[0-9])\/(3[0-1]|[0-2][0-9])\/(19[7-9][0-9]|20[0-9]{2})(|\ [0-9]{1,2}:[0-9]{1,2})))$/;

        var dateDaysRegex = /^((1[0-2]|0[0-9])\/(3[0-1]|[0-2][0-9])\/(19[7-9][0-9]|20[0-9]{2})|[0-9]{1,2}(|,[0-9]{1,2}))$/;

        var dateTimeRegex = /^(|(1[0-2]|0[0-9])\/(3[0-1]|[0-2][0-9])\/(19[7-9][0-9]|20[0-9]{2}))(|( |)[0-9]{1,2}(|:[0-9]{1,2}))$/;

        var timeDurationRegex = /^[0-9]{1,2}(|:[0-9]{1,2})$/;

        var daysDurationRegex = /^[0-9]{1,2}(|,[0-9]{1,2})$/;

        Ext.apply(Ext.form.field.VTypes, {
            //Date or Duration: mm/dd/yyyy or Days.Hours or Hours:Minutes or mm/dd/yyyy Hours:Minutes
            dateDuration: function(val, field) {
                return dateDurationRegex.test(val);
            },
            dateDurationText: 'Not a valid duration. Must be in the format "0.0".',
            dateDurationMask: /[0-9,\/\ :]/,

            // Date or Duration : mm/dd/yyyy or Days.Hours
            dateDays: function(val, field) {
                return dateDaysRegex.test(val);
            },
            dateDaysText: 'Not a valid duration. Must be in the format "0.0".',
            dateDaysMask: /[0-9,\/\ :]/,

            // Date, Time, Date and Time : mm/dd/yyyy H:i
            dateTime: function(val, field) {
                return dateTimeRegex.test(val);
            },
            dateTimeText: 'Not a valid duration. Must be in the format "0:0".',
            dateTimetMask: /[0-9:\/]/,

            // Time H:i
            timeDuration: function(val, field) {
                return timeDurationRegex.test(val);
            },
            timeDurationText: 'Not a valid duration. Must be in the format "00:00".',
            timeDurationtMask: /[0-9\:]/,

            // Duration Days:Hours
            daysDuration: function(val, field) {
                return daysDurationRegex.test(val);
            },
            daysDurationText: 'Not a valid duration. Must be in the format "00:00".',
            daysDurationtMask: /[0-9,]/
        });
    }
});
```