---
title: รายชื่อโรคติดต่อในละอองลอยในอดีต
permalink: /th/historical-list
layout: page
---

<script
  src="https://code.jquery.com/jquery-3.6.0.min.js"
  integrity="sha256-/xUj+3OJU5yExlq6GSYGSHk7tPXikynS7ogEvDej/m4="
  crossorigin="anonymous"></script>
<script type="text/javascript" src="https://cdn.datatables.net/1.10.11/js/jquery.dataTables.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/fixedcolumns/3.2.1/js/dataTables.fixedColumns.min.js"></script>
<script src="https://unpkg.com/dayjs@1.8.21/dayjs.min.js"></script>
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.10.25/css/jquery.dataTables.min.css">

มีการพูดคุยกันถึงลักษณะของการติดเชื้อในอากาศหรือละอองลอยสำหรับโรคอื่น ๆ ในช่วงหลายปีที่ผ่านมา และรายการนี้ประกอบด้วยการพัฒนาที่สำคัญหลายประการในหัวข้อเหล่านี้  <a href="https://twitter.com/intent/tweet?url=https%3A%2F%2Fits-airborne.org%2Fhistorical-list&via=AerosolizedC19&text=%23COVIDisAirborne%20%23masks4All%20%23bewareOfSharedAir%20%23ventilation. See: " target="_blank">ทวีตหน้านี้</a>

เพื่อประโยชน์ของไทม์ไลน์นี้ **ละอองลอย** = **ในอากาศ** = **นิวเคลียสของหยด** อนุภาคเหล่านี้เป็นอนุภาคที่มีเส้นผ่านศูนย์กลางน้อยกว่า 100 ไมโครเมตร ดังนั้นโดยทั่วไปจะระเหยไปก่อนที่แรงโน้มถ่วงจะดึงพวกมันลงสู่พื้น ในฐานะที่เป็นอนุภาคขนาดเล็ก พวกมันจะลอยเป็นนาทีหรือเป็นชั่วโมง และสามารถเดินทางได้ไกลในเวลานี้ คำว่าละอองลอยหมายถึงอนุภาคที่ลอยอยู่ในอากาศ

ในทางกลับกัน **หยด** อนุภาคเหล่านั้นที่มีเส้นผ่านศูนย์กลางใหญ่กว่า 100 ไมโครเมตร มักจะถูกแรงโน้มถ่วงดึงลงมาที่พื้น ซึ่งกล่าวกันว่าเกิดขึ้นภายในสองเมตร โดยปกติ - ก่อนที่พวกมันจะระเหยและลอยตัว


หมายเหตุ: ชุมชนทางการแพทย์และวิทยาศาสตร์กำลังเปลี่ยนเป็นคำจำกัดความ **100** μm (และสูงกว่า) ของหยด เดิมคือ **5** μm . <a target="_blank" href="https://twitter.com/linseymarr/status/1336318245348003840">See @linseymarr's tweets</a>. ทุกอย่างที่มีขนาดเล็กกว่า 100 μm เป็นละอองลอย ดูเพิ่มเติมที่เวอร์ชัน [ไทม์ไลน์](historical-timeline.html) ของหน้านี้

<script>
$(document).ready(function () {
    $.noConflict();

       $.getJSON("../media/aerosol-history-timeline.json", function(tl) {
            for(i=0;i < tl.events.length;i++){
                    var html='';
                    var dt = tl.events[i].start_date.year; 
                    var mt = tl.events[i].start_date.month;
                    var dy = tl.events[i].start_date.day;
                    if (mt > 0) {
                        dt = dt + "-" + mt;     
                        if (dy > 0) {
                            dt = dayjs(dt + "-" + dy).format('MMM D, YYYY');     
                        } else {
                            dt = dayjs(dt + "-1").format('MMM, YYYY');    
                        }
                    }

                    dt = dt.replaceAll("-undefined","");
                    html +='<td>' + dt +'</td>';
                    html +='<td><a href="' + tl.events[i].media.link +'">link</a></td>';
                    html +='<td>' + tl.events[i].text.headline +'</td>';
                    html +='<td>' + tl.events[i].text.text +'</td>';
                    $('#table_id tbody').append('<tr>'+html+'</tr>');
            }
            $('#table_id').DataTable();
       });
});
</script>

<table id="table_id" class="display">
    <thead>
        <tr>
          <th>วันที่</th>
          <th>ลิงค์</th> 
          <th>หัวข้อข่าว</th> 
          <th>ข้อความ</th>
        </tr>
    </thead>
    <tbody>        
    </tbody>
</table>