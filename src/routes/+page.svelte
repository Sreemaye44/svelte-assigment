
  <div class="grid md:grid-cols-2 h-screen">
  <!-- left part -->
<div class="grid md:grid-row-6 bg-rose-100">
  <!-- upper part -->
  <div class="row-span-5 grid grid-cols-3">
  <div class="grid grid-row-1">
    <div class="bg-blue-400 hidden md:block row-span-3"></div>
    <div class="bg-teal-400 hidden md:block row-span-2"></div>
   
  </div>
  <div class="bg-rose-100 col-span-2"></div>
</div>
<!-- lower part -->
<div class="bg-fuchsia-400 hidden md:block"></div>
</div>
<!-- right part -->
<div class=" grid md:grid-rows-3">
  <div class="bg-blue-400 hidden md:block"></div>
  <div class="row-span-2 grid grid-cols-3">
    <!-- mountain home -->
    <div class="bg-yellow-100 col-span-3 md:col-span-2 grid place-items-center">
           <div class="h-[300px] w-[300px] bg-[#293462] grid place-items-center">
            <div class="inner-circle">
<div class="big-box"></div>
<div class="smaller-box"></div>
            </div>
           </div>
    </div>
    <div class="bg-emerald-400 hidden md:block"></div>
  </div>
</div>
  </div>

  <style>

.inner-circle{
  width: 200px;
  height: 200px;
  border-radius: 50%;
  background-color: #FFF1C1;
  overflow: hidden;
  position: relative;
}
.big-box{
      width: 0px;
      height: 0px;
      border-bottom: 200px solid #FE5F55;
      border-right: 200px solid transparent;
      border-left: 200px solid transparent;
      position: absolute;
      top: 59px;
      left: -59px;

    }
.smaller-box{
      width: 0px;
      height: 0px;
      border-bottom: 100px solid #FE5F55;
      border-right: 100px solid transparent;
      border-left: 100px solid transparent;
      position: absolute;
      top: 129px;
      left: -71px;

    }
  </style>


