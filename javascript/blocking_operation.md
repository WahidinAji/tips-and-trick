## both of them still relevant ini this abad 21 wkwkw
* bagus ketika ngga ada blocking operation, mau menghindari flicker, dan tidak ada hoisting
  - `script harus di taro di buntut`
  - `bagus buat atur life cycle declaration`
 
 ```js
 <script>
    document.addEventListener('DOMContentLoaded', function() {
        let calendarEl = document.getElementById('calendar');
        let events = [
            {
                'title' => 'Repeating Event',
                'url' => 'http://google.com/',
                'start' => '2022-04-21T16:00:00'
            },
            {
                'title' => 'Meeting',
                'url' => 'http://google.com/',
                'start' => '2022-04-21T10:30:00',
                'end' => '2022-04-21T12:30:00'
            },
            {
                'title' => 'Lunch',
                'url' => 'http://google.com/',
                'start' => '2022-04-22T12:00:00'
            },
            {
                'title' => 'Meeting',
                'url' => 'http://google.com/',
                'start' => '2022-04-22T14:30:00'
            },
            {
                'title' => 'Happy Hour',
                'url' => 'http://google.com/',
                'start' => '2022-04-21T17:30:00'
            },
            {
                'title' => 'Dinner',
                'url' => 'http://google.com/',
                'start' => '2022-04-21T20:00:00'
            },
            {
                'title' => 'Birthday Party',
                'url' => 'http://google.com/',
                'start' => '2022-04-21T07:00:00'
            },
            {
                'title' => 'Click for Google',
                'url' => 'http://google.com/',
                'start' => '2022-04-23T07:00:00'
            },
        ];

        let calendar = new FullCalendar.Calendar(calendarEl, {
            plugins: ['interaction', 'dayGrid', 'timeGrid', 'list'],
            header: {
                left: "dayGridMonth,timeGridWeek,listDay",
                right: "prev,title,next"
            },
            views: {
                listDay: {
                    buttonText: 'day'
                }
            },
            defaultDate: Date.now(),
            navLinks: true, // can click day/week names to navigate views
            editable: true,
            eventLimit: true, // allow "more" link when too many events
            events: events,
            contentHeight: 600,
            dateClick: function(info) {
                let url = "{{ route('erph.daily.index', $erph_class->slug) }}" + '?date=' + info.dateStr;
                window.location.href = url;
            },
        });

        calendar.render();
    });
</script>
 ```
 
  - Sample in blade

![image](https://user-images.githubusercontent.com/48281037/164372160-0046aa36-5ad5-43ef-b60d-a8c462fe3af9.png)


* bagus ketika ada blocking operation, ngga peduli flicker, dan males atur declaration
  - `biarpun script-nya di taro di head bakalan tetep jalan normal`

```js
 <script>
    let calendarEl = document.getElementById('calendar');
    let events = [
        {
            'title' => 'Repeating Event',
            'url' => 'http://google.com/',
            'start' => '2022-04-21T16:00:00'
        },
        {
            'title' => 'Meeting',
            'url' => 'http://google.com/',
            'start' => '2022-04-21T10:30:00',
            'end' => '2022-04-21T12:30:00'
        },
        {
            'title' => 'Lunch',
            'url' => 'http://google.com/',
            'start' => '2022-04-22T12:00:00'
        },
        {
            'title' => 'Meeting',
            'url' => 'http://google.com/',
            'start' => '2022-04-22T14:30:00'
        },
        {
            'title' => 'Happy Hour',
            'url' => 'http://google.com/',
            'start' => '2022-04-21T17:30:00'
        },
        {
            'title' => 'Dinner',
            'url' => 'http://google.com/',
            'start' => '2022-04-21T20:00:00'
        },
        {
            'title' => 'Birthday Party',
            'url' => 'http://google.com/',
            'start' => '2022-04-21T07:00:00'
        },
        {
            'title' => 'Click for Google',
            'url' => 'http://google.com/',
            'start' => '2022-04-23T07:00:00'
        },
    ];

    let calendar = new FullCalendar.Calendar(calendarEl, {
        plugins: ['interaction', 'dayGrid', 'timeGrid', 'list'],
        header: {
            left: "dayGridMonth,timeGridWeek,listDay",
            right: "prev,title,next"
        },
        views: {
            listDay: {
                buttonText: 'day'
            }
        },
        defaultDate: Date.now(),
        navLinks: true, // can click day/week names to navigate views
        editable: true,
        eventLimit: true, // allow "more" link when too many events
        events: events,
        contentHeight: 600,
        dateClick: function(info) {
            let url = "{{ route('erph.daily.index', $erph_class->slug) }}" + '?date=' + info.dateStr;
            window.location.href = url;
        },
    });

    calendar.render();
</script>
 ```
 
  - Sample in blade
 
![image](https://user-images.githubusercontent.com/48281037/164372219-97a69f13-fd8c-4585-bce2-f824b79f2b42.png)


