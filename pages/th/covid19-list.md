---
title:  รายชื่อสเปรย์โควิด-19
permalink: /th/covid19-list
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

กิจกรรมและบทความที่เกี่ยวข้องที่สนับสนุนลักษณะละอองลอยของการติดเชื้อโควิด-19 ไวรอนมีขนาดประมาณ 0.115 ไมครอน และแขวนลอยในของเหลวที่มีน้ำเป็นละอองขนาด 0.7 ไมครอนขึ้นไป **หากประเทศของคุณยังไม่แพร่ระบาด COVID-19 คุณควรสวมหน้ากากผ้าที่ดี (หรือหน้ากาก) ให้มากที่สุดเมื่ออยู่ร่วมกับผู้อื่นในบ้านและในพื้นที่ที่มีการระบายอากาศไม่ดี** #covidIsAirborne #masks4All #bewareOfSharedAir #ventilation. <a href="https://twitter.com/intent/tweet?url=https%3A%2F%2Fits-airborne.org%2Fth%2Fcovid19-list&via=AerosolizedC19&text=%23COVIDisAirborne%20%23masks4All%20%23bewareOfSharedAir%20%23ventilation. See: " target="_blank">ทวีตหน้านี้</a>. ดูเพิ่มเติมที่เวอร์ชัน [ไทม์ไลน์](covid19-timeline.html) ของหน้านี้

<script>
$(document).ready(function () {
    $.noConflict();

       $.getJSON("../media/aerosol-timeline.json", function(tl) {
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