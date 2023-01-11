<style>
p{
    font-family: Georgia;
    font-size: 50px;
}
.right {
  float: right;
  padding: 10px;
}
.container {
  width: auto;
  display: flex;
  flex-direction: column;
}
.btn {
  margin: 20px auto;
  border: none;
  padding: 10px 44px;
  font-size: 36px;
  position: relative;
}
.btn::before {
  transition: all 0.85s cubic-bezier(0.68, -0.55, 0.265, 1.55);
  content: "";
  width: 50%;
  height: 100%;
  background: black;
  position: absolute;
  top: 0;
  left: 0;
}
.btn .btn-text {
  color: white;
  mix-blend-mode: difference;
}
.btn:hover::before {
  background: black;
  width: 100%;
}
.btn.rounded {
  border-radius: 50px;
}
.btn.rounded .text-green {
  color: #00F0B5;
  mix-blend-mode: difference;
}
.btn.rounded::before {
  border-radius: 50px;
  width: 25%;
  background: #00F0B5;
}
.btn.rounded:hover::before {
  background: #00F0B5;
  width: 100%;
}

#inp {
  position: relative;
  margin: auto;
  width: 100%;
  max-width: 280px;
  border-radius: 3px;
  overflow: hidden;
}
#inp .label {
  position: absolute;
  top: 20px;
  left: 12px;
  font-size: 16px;
  color: rgba(0, 0, 0, 0.5);
  font-weight: 500;
  transform-origin: 0 0;
  transform: translate3d(0, 0, 0);
  transition: all 0.2s ease;
  pointer-events: none;
}
#inp .focus-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.05);
  z-index: -1;
  transform: scaleX(0);
  transform-origin: left;
}
#inp input {
  -webkit-appearance: none;
  -moz-appearance: none;
       appearance: none;
  width: 100%;
  border: 0;
  font-family: inherit;
  padding: 16px 12px 0 12px;
  height: 56px;
  font-size: 16px;
  font-weight: 400;
  background: rgba(0, 0, 0, 0.02);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.3);
  color: #000;
  transition: all 0.15s ease;
}
#inp input:hover {
  background: rgba(0, 0, 0, 0.04);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.5);
}
#inp input:not(:-moz-placeholder-shown) + .label {
  color: rgba(0, 0, 0, 0.5);
  transform: translate3d(0, -12px, 0) scale(0.75);
}
#inp input:not(:-ms-input-placeholder) + .label {
  color: rgba(0, 0, 0, 0.5);
  transform: translate3d(0, -12px, 0) scale(0.75);
}
#inp input:not(:placeholder-shown) + .label {
  color: rgba(0, 0, 0, 0.5);
  transform: translate3d(0, -12px, 0) scale(0.75);
}
#inp input:focus {
  background: rgba(0, 0, 0, 0.05);
  outline: none;
  box-shadow: inset 0 -2px 0 #0077FF;
}
#inp input:focus + .label {
  color: #0077FF;
  transform: translate3d(0, -12px, 0) scale(0.75);
}
#inp input:focus + .label + .focus-bg {
  transform: scaleX(1);
  transition: all 0.1s ease;
}
</style>
<script>
  function getYear(){
      let inputYear = document.getElementById("inputYear").value;
      return inputYear;
  }
  function isLeapYear(year) {
      result = document.getElementById("isLeapYearResult");
      // Fetch data from API
      fetch('http://spiderbiters.nighthawkcodingsociety.com/api/calendar/isLeapYear/' + year)
      .then(response => response.json())
      .then(data =\> {
          console.log(data);
          result.innerHTML = "Is " + year + " a leap year: " + data.isLeapYear;
      })
  }
</script>
<body>
  <div class="container">
    <p>Is it a leap year?: </p>
    <label for="inp" id="inp">
      <input id="inputYear" class="inp">
      <span class="label">Year</span>
      <span class="focus-bg"></span>
    </label>
  </div>
  <div class="container">
    <button onclick="isLeapYear(getYear())" class="btn rounded"><span class="text-green">Check</span></button>
    <p id="isLeapYearResult"></p>
  </div>
</body>