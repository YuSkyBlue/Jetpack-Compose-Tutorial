# Jetpack-Compose-Tutorial

<img src="https://velog.velcdn.com/images/workspace/post/242af9e8-77be-432f-b1f3-71eff291b781/android-jetpack-header.png" width="500" height ="300"><br>
<h2>🍎1 Chapter</h2>
  
<h3>Column</h3>
  <h4>verticalArragement </h4><br> 
  <li>Arrangement.Top</li>
  <li>Arrangement.Center</li>
  <li>Arrangement.Bottom</li>
  li> Arrangement.SpaceBetween</li>
  <li>Arrangement.SpaceAround</li>
  <li>Arrangement.SpaceEvenly</li>
  
  <h4>horizontalAlignment</h4>
 
  
 <h3>Row</h3> 
 - horizontalArrangement
 - verticalAlignment
  
  
 <h2>🍎2 Chapter</h2>
 <li>border / offset<li>
 <li>fillMaxWidth</li>
  <li>fillMaxSize</li>

 <h2>🍎3 Chapter</h2> 
 <h3> Card</h3>
 <li>RoundCornerShape</li>
  <li>elevation</li>
  
<h3>Box</h3>
 <li>painter </li>
 <li>contentScale</li>
 <li>contentAlignment</li>
 <li>Brush.verticalGradient / startY</li>

<h2>🍎4 Chapter</h2>
<li>fontFamily</li>
<li>buildAnnotatedString</li>
<li>withStyle / append</li>
<li>TextDecoration</li>

 <h2>🍎5 Chapter</h2>
<li>TextField / label</li>
<li>onValueChange</li>
<li>scafooldState / append</li>
<li>showSnackbar</li>

<h2>🍎6 Chapter</h2>
<li>itemsIndex / items</li>
<li>why have to use LazyColumn</li>
<li>scrollState</li>

<h2>🍎7 Chapter</h2>
<li>ConstrainSet ex) greenBox / redBox</li>
<li>createHorizontalChain </li>
<li>ConstrainLayout( constrainst, modifier= ~~)</li>
~~~kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        setContent {
            val constraints = ConstraintSet {
                val greenBox = createRefFor("greenBox")
                val redBox = createRefFor("redBox")
//                val guildline= createGuidelineFromTop(0.5f)

                constrain(greenBox) {
//                    top.linkTo(guildline)
                    top.linkTo(parent.top)
                    start.linkTo(parent.start)

                    width = Dimension.value(100.dp)
                    height = Dimension.value(100.dp)
                }
                constrain(redBox) {
                    top.linkTo(parent.top)
                    start.linkTo(greenBox.end)
                    end.linkTo(parent.end)
                    width = Dimension.value(100.dp)
                    height = Dimension.value(100.dp)
                }
                createHorizontalChain( greenBox, redBox, chainStyle = ChainStyle.Packed)

            }
            ConstraintLayout(constraints, modifier = Modifier.fillMaxWidth()){
                Box(modifier = Modifier
                    .background(Color.Green)
                    .layoutId("greenBox"))
                Box(modifier = Modifier
                    .background(Color.Red)
                    .layoutId("redBox"))

            }
        }
    }
}

~~~
