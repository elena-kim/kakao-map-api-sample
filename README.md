```javascript
<div id="map" style="width:100%;height:700px;"></div>
<style>
    .customoverlay {
            position:relative;
            bottom:85px;
            border-radius:6px;
            border: 1px solid #ccc;
            border-bottom:2px solid #ddd;
            float:left;
        }
    .customoverlay .title {
            display:block;
            text-align:center;
            background:#fff;
        	border-radius:6px;
            margin-right:0px;
            padding:10px 15px;
            font-size:14px;
            font-weight:bold;
        }
    .customoverlay:after {
            content:'';
            position:absolute;
            margin-left:-12px;
            left:50%;
            bottom:-12px;
            width:22px;
            height:12px;
            background:url('https://t1.daumcdn.net/localimg/localimages/07/mapapidoc/vertex_white.png')
        }
    .customoverlay:nth-of-type(n) {
        border:0; 
        box-shadow:0px 1px 2px #888;
    }
	</style>
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
    
    // 커스텀 오버레이에 표출될 내용으로 HTML 문자열이나 document element가 가능합니다
    var content =  '<div class="customoverlay">' +
    '    <span class="title">' + positions[i].title + '</span>'
    '</div>';
    // 커스텀 오버레이가 표시될 위치입니다 
    var position = positions[i].latlng;
    
    // 커스텀 오버레이를 생성합니다
    var customOverlay = new kakao.maps.CustomOverlay({
        map: map,
        position: position,
        content: content,
        yAnchor: 0 
    });
}
</script>
```

![image](https://user-images.githubusercontent.com/74305823/203701875-d7ef048b-e8e4-48ef-b086-5324a81f4613.png)
