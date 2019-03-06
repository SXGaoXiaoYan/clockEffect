# clockEffect
时钟的效果

<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;padding: 0;
			}
			.bp{
				width: 200px;height: 200px;border: 1px solid black;border-radius: 100%;margin: 50px auto;position: relative;
			}
			.kedu{
				width: 1px;height: 10px;background: black;position: absolute;left: 100px;top: 0px;transform-origin: 0px 100px;
			}
			.shuzi{
				position: absolute;width: 10px;font-size: 10px;height: 85px;transform-origin:bottom ;top: 15px;left: 95px;
			}
			.scd{
				width: 1px;height: 70px;position: absolute;left: 100px;top: 30px;transform-origin:bottom;background: red;
			}
			.min{
				width: 2px;height: 60px;position: absolute;left: 99px;top: 40px;transform-origin:bottom;background: black;
			}
			.hour{
				width: 3px;height: 50px;position: absolute;left: 98.5px;top: 50px;transform-origin:bottom;background: black;
			}
		</style>
	</head>
	<body>
		<div class="bp">
			<div class="hour"></div>
			<div class="min"></div>
			<div class="scd"></div>
		</div>
	</body>
	<script type="text/javascript">
		var bp = document.querySelector(".bp");
		var h = document.querySelector(".hour");
		var m = document.querySelector(".min");
		var s = document.querySelector(".scd");
		var date = new Date();
		var hours = date.getHours();
		var min = date.getMinutes();
		var scd = date.getSeconds();
		var hk = hours*30+min*0.5;
		h.style.transform = "rotateZ("+hk+"deg)";
		m.style.transform = "rotateZ("+min*6+"deg)";
		s.style.transform = "rotateZ("+scd*6+"deg)";
		for (var i = 0 ; i < 60 ; i++) {
			var kd = document.createElement("div");
			kd.className="kedu";
			bp.appendChild(kd);
		}
		for (var i = 0 ; i < 12 ; i++) {
			var shuzi = document.createElement("div");
			shuzi.className="shuzi"
			shuzi.style.transform = "rotateZ("+(i+1)*30+"deg)";
			var num = document.createElement("div");
			num.innerHTML = i+1;
			num.style.textAlign = "center";
			num.style.transform = "rotateZ("+(i+1)*-30+"deg)";
			shuzi.appendChild(num)
			bp.appendChild(shuzi)
		}
		function keduchi(){
			var kds = document.querySelectorAll(".kedu");
			for (var i = 0 ; i < kds.length ; i++) {
				kds[i].style.transform = 'rotateZ('+6*i+'deg)';
				if (i%5==0) {
					kds[i].style.height = 15+"px"
				}
			}
		}
		keduchi()
		var md = 0;
		setInterval(function(){
			var date2 = new Date();
			var ss = date2.getSeconds();
			if (ss%60==0) {
				md++;
				var mds = min*6+6*md;
				m.style.transform="rotateZ("+mds+"deg)";
				var hds = hk+0.5*md;
				h.style.transform="rotateZ("+hds+"deg)";
			}
			s.style.transform="rotateZ("+ss*6+"deg)";
		},1000)
	</script>
</html>

