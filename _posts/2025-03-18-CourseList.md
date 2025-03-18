---
title: CourseList
date: 2025-03-18 11:16:00 +0330
categories: [University, Schedule]
tags: [universiy,classes,timetable,amozeshyar]     # TAG names should always be lowercase
---
---
description: Course offered in second term 1403-1404 
---
---
pin: true
---

# لیست دروس ارائه شده

**آخرین بروزرسانی:** 27 بهمن 1403  

## نمایش هفتگی

### شنبه
| نام درس | کد درس | زمان کلاس | استاد | تعداد واحد | حداکثر ظرفیت | مقطع | کد ارائه | زمان امتحان | مکان برگزاری | گروه آموزشی |
|---|---|---|---|---|---|---|---|---|---|---|
| کارگاه کامپیوتر | 7000031553 | شنبه از 19:30 تا 20:50 | نشمين افضلي | 1.0 | 8 | کارشناسی پیوسته | استاد یوسف سنائی | - | - | گروه کامپیوتر (2110130) |

## تمام دروس

| نام درس | کد درس | زمان کلاس | استاد | تعداد واحد | حداکثر ظرفیت | مقطع | کد ارائه | زمان امتحان | مکان برگزاری | گروه آموزشی | شماره |
|---|---|---|---|---|---|---|---|---|---|---|---|
| یکپارچه سازی کاربردهای سازمانی | 4628162051 | چهارشنبه 13:00 تا 15:40 | نگار شهابي | 3.0 | 45 | کارشناسی پیوسته | آزیتا شیرازی پور | 1404/03/17 از 14:00 تا 15:30 | فنی و مهندسی-1404 | گروه کامپیوتر (2110130) | 1924 |

[مشاهده مخزن در گیت‌هاب](https://github.com/abolfazlvahed1/AmozeshyarTimetable)

```html
<script>
    function switchView(viewName) {
        document.querySelectorAll('.view-controls .button').forEach(btn => {
            btn.classList.remove('active');
        });
        event.target.classList.add('active');

        document.querySelectorAll('.view').forEach(view => {
            view.classList.remove('active');
        });
        document.getElementById(viewName + 'View').classList.add('active');

        filterCourses();
    }

    function filterCourses() {
        const filterValue = document.getElementById('filterInput').value.trim();
        const filters = filterValue.split('-').map(f => f.trim()).filter(f => f);

        const matchesCourse = (courseRow) => {
            if (filters.length === 0) return true;
            const text = courseRow.textContent.toLowerCase();
            return filters.some(filter => text.includes(filter.toLowerCase()));
        };

        const activeView = document.querySelector('.view.active');
        if (activeView.id === 'weeklyView') {
            activeView.querySelectorAll('tr:not(:first-child)').forEach(row => {
                row.classList.toggle('hidden', !matchesCourse(row));
            });

            activeView.querySelectorAll('h2').forEach(header => {
                const table = header.nextElementSibling;
                const visibleRows = table.querySelectorAll('tr:not(.hidden)').length - 1;
                header.style.display = visibleRows > 0 ? '' : 'none';
                table.style.display = visibleRows > 0 ? '' : 'none';
            });
        } else if (activeView.id === 'allView') {
            const rows = activeView.querySelectorAll('table tbody tr');
            rows.forEach(row => {
                row.classList.toggle('hidden', !matchesCourse(row));
            });
        }
    }
</script>
