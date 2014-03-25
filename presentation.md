<img src="images/logo.png">
## Passive data.  Realtime health.
### hello@realize.pe

---
= data-background='images/vision_background.jpg'

## Vision

## A world where everyone is fully in control of themselves.

---

## Everyone wants to improve their health and avoid hospital stays.  They often just don't know how.

### Patients lack:

* *Timely information.*  The process for discovering that you have an illness often involves experiencing a symptom and looking it up online.
* *Quick connections to caregivers.*  Healthcare organizations are currently unable to influence patient behavior when they aren't in the office.
* *Personalized insight.* Recovery is usually one-size-fits all, and can't adapt to the individual.

---

## How do we solve this?

* *Trend:* Patients increasingly use wearable devices to track their health
* *Trend:* Hospitals are increasingly incentivized to favor preventative and lower-cost care
* *Solution:* Leverage patient health data to increase engagement and make care more effective

---

## Product

### An open source, extensible web platform that aggregates and analyzes health data

* *Easy-to-use dashboard.*  Lets patients see their data at a glance
* *Powerful administrative tools.*  Makes it easy for hospitals and clinics to manage patients
* *Plugin architecture.*  Lets developers can write plugins that pull in data from trackers, analyze it, and display it to the user
* *Full API.*  Enables mobile apps to leverage the capabilities of the platform

---

## Impacts

* Help patients by providing timely analysis and insight
* Help hospitals by enabling real-time patient monitoring and intervention
* Help developers by making it much easier to make mobile health apps

---

## Market Size

* Huge shift in healthcare policy with Affordable Care Act
    * Emphasize patient satisfaction and preventative care
    * 606 Accountable Care Organizations (ACOs) in Q4 2013 (Health Affairs)
    * 18 million insured through ACOs (Health Affairs)

* Large growth in self-tracking
    * 35 million total US self-trackers (Pew Research)

* 4.3 million preventable hospitalizations yearly in the US (CDC)
* Cost of $10,000 per hospital stay (AHRQ)

---

## Long Term

* The trend towards lowering hospital costs and increasing patient satisfaction metrics shows no sign of slowing down
    * The number of ACOs is growing by 11% per quarter
    * Medicare is moving to tie doctor bonuses to patient satisfaction

* Wearable device adoption is vastly increasing
    * Wearable device numbers are growing by more than 100% a year (Berg Insight)

---

## Business Model

* Recurring subscriptions
    * Individuals and organizations pay a per-month hosting fee

* App store model
    * We take a 30% cut of plugins sold by developers on the plugin store

---

## Team

* Vik Paruchuri, co-founder
    * http://www.linkedin.com/in/vikparuchuri
    * Winner of 3 Kaggle competitions on automated essay scoring and bond price prediction
    * Machine learning and web development at edX; created ways to assess essays and short responses at scale
    * US diplomat stationed in South America
    * B.A. in American History from the University of Maryland

* Adam Laughlin, co-founder
    * http://www.linkedin.com/in/alaughlin
    * Front-end web developer for Scratch, an MIT learning tool used by millions of students
    * Boston Quantified Self Organizer
    * Co-founded Web Analysts Without Borders at Save the Children
    * B.A. in Psychology from Hope College

---

## Milestones

* Finish prototype (April 2014)
* Launch with our initial partners (April 2014)
* Start our initial physician pilots (June 2014)
* Start our first hospital pilot (August 2014)
* Conclude hospital pilot (January 2015)
* Roll out into first hospital (March 2015)

---

## Financials

<div class="chart-panel" data-x="[1402790400, 1410674400, 1418558400, 1426442400, 1434326400, 1442210400, 1450094400, 1457978400, 1465862400, 1473746400, 1481630400, 1489514400, 1497398400, 1505282400, 1513166400]" data-y="[1136, 3045, 7673, 9703, 12336, 390827, 470513, 552010, 636328, 725243, 821878, 1006833, 1215417, 1466485, 1795073]">
    <div class="chart">
        <svg style="height: 500px"></svg>
    </div>
</div>




<script src="http://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js" type="text/javascript"></script>
<script src="http://cdnjs.cloudflare.com/ajax/libs/d3/3.4.3/d3.min.js" type="text/javascript"></script>
<script src="http://cdnjs.cloudflare.com/ajax/libs/nvd3/1.1.14-beta/nv.d3.min.js" type="text/javascript"></script>

<script>
$(document).ready(function(){
    $(".chart-panel").each(function(){
        var that = this;
        nv.addGraph(function() {
            var chart = nv.models.lineChart()
                    .margin({left: 200})  //Adjust chart margins to give the x-axis some breathing room.
                    .useInteractiveGuideline(true)  //We want nice looking tooltips and a guideline!
                    .transitionDuration(350)  //how fast do you want the lines to transition?
                    .showLegend(false)       //Show the legend, allowing users to turn on/off line series.
                    .showYAxis(false)
                ;

            chart.xAxis.axisLabel('Date').tickFormat(function(d) {
                return d3.time.format("%m/%y")(new Date(d * 1000))
            });

            chart.yAxis     //Chart y-axis settings
                .axisLabel('')
                .tickFormat(d3.format('$d'));

            var x = $(that).data("x");
            var y = $(that).data("y");

            var newData = [];
            for(var i=0;i< x.length;i++){
                newData.push({x: parseFloat(x[i]), y: parseFloat(y[i])})
            }

            var chartData = [
                {
                    values: newData,      //values - represents the array of {x,y} data points
                    key: 'Metric' //key  - the name of the series.
                },
            ];
            d3.select($(that).find(".chart svg")[0])    //Select the <svg> element you want to render the chart in.
                .datum(chartData)         //Populate the <svg> element with chart data...
                .call(chart);          //Finally, render the chart!

            console.log("Charting done");
            //Update the chart when window resizes.
            nv.utils.windowResize(function() { chart.update() });
            return chart;
        });
    });
});
</script>

<style>
.tick, .nv-axisMaxMin{
font-size: 15px !important;
}
.nv-axislabel {
font-size: 20px !important;
}
</style>