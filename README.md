```javascript
<div id="map" style="width:100%;height:600px;"></div>
<script>
var mapContainer = document.getElementById('map'), // 지도를 표시할 div  
    mapOption = { 
        center: new kakao.maps.LatLng(37.486608, 127.121845), // 지도의 중심좌표
        level: 6 // 지도의 확대 레벨
    };

var map = new kakao.maps.Map(mapContainer, mapOption); // 지도를 생성합니다
 
// 마커를 표시할 위치와 title 객체 배열입니다 
var positions = [
    {
        title: '잠실', 
        latlng: new kakao.maps.LatLng(37.5139846856461, 127.10061197159)
    },
    {
        title: '송파', 
        latlng: new kakao.maps.LatLng(37.499465, 127.112006)
    },
    {
        title: '문정', 
        latlng: new kakao.maps.LatLng(37.486608, 127.121845)
    },
    {
        title: '장지',
        latlng: new kakao.maps.LatLng(37.478288, 127.126078)
    },
    {
        title: '오금',
        latlng: new kakao.maps.LatLng(37.50883102, 127.1342621)
    }
];

// 마커 이미지의 이미지 주소입니다
var imageSrc = "https://t1.daumcdn.net/localimg/localimages/07/mapapidoc/markerStar.png"; 
    
for (var i = 0; i < positions.length; i ++) {
    
    // 마커 이미지의 이미지 크기 입니다
    var imageSize = new kakao.maps.Size(24, 35); 
    
    // 마커 이미지를 생성합니다    
    var markerImage = new kakao.maps.MarkerImage(imageSrc, imageSize); 
    
    // 마커를 생성합니다
    var marker = new kakao.maps.Marker({
        map: map, // 마커를 표시할 지도
        position: positions[i].latlng, // 마커를 표시할 위치
        //title : positions[i].title, // 마커의 타이틀, 마커에 마우스를 올리면 타이틀이 표시됩니다
        image : markerImage // 마커 이미지 
    });
    
    // 인포윈도우
    var iwContent =  '<div class="customoverlay">' +
    '    <span class="title">' + positions[i].title + '</span>'
    '</div>', // 인포윈도우에 표출될 내용으로 HTML 문자열이나 document element가 가능합니다
    iwPosition = positions[i].latlng;
    
   var customOverlay = new kakao.maps.CustomOverlay({
        map: map,
        position: iwPosition,
        content: iwContent,
        yAnchor: 2 
    });
    
    // 인포윈도우를 생성합니다
    //var infowindow = new kakao.maps.InfoWindow({
    //    position : iwPosition, 
    //    content : iwContent 
	//});
    // 마커 위에 인포윈도우를 표시합니다. 두번째 파라미터인 marker를 넣어주지 않으면 지도 위에 표시됩니다
	//infowindow.open(map, marker); 
}
</script>
```

```css
.customoverlay {position:relative;bottom:85px;border-radius:6px;border: 1px solid #ccc;border-bottom:2px solid #ddd;float:left;}
.customoverlay:nth-of-type(n) {border:0; box-shadow:0px 1px 2px #888;}
.customoverlay a {display:block;text-decoration:none;color:#000;text-align:center;border-radius:6px;font-size:14px;font-weight:bold;overflow:hidden;background: #d95050;background: #d95050 url(https://t1.daumcdn.net/localimg/localimages/07/mapapidoc/arrow_white.png) no-repeat right 14px center;}
.customoverlay .title {display:block;text-align:center;background:#fff;margin-right:35px;padding:10px 15px;font-size:14px;font-weight:bold;}
.customoverlay:after {content:'';position:absolute;margin-left:-12px;left:50%;bottom:-12px;width:22px;height:12px;background:url('https://t1.daumcdn.net/localimg/localimages/07/mapapidoc/vertex_white.png')}
```
