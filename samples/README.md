# Qualitative Examples

## MMBench

<table class="center">
	<tr>
		<td style="text-align:center;", colspan="2"><b>Logic Reasoning:<br>Structuralized Imagetext Understanding</b></td>
		<td style="text-align:center;", colspan="2"><b>Finegrained Perception (cross-instance):<br>Action Recognition</b></td>
	</tr>
	<tr>
		<td colspan="2"><img src="MMBench/1.jpg"></td>
		<td colspan="2"><img src="MMBench/21.jpg"></td>
	</tr>
	<tr>
		<td colspan="2"><p>QUESTION.&nbsp;What&nbsp;is&nbsp;correct&nbsp;Python&nbsp;code&nbsp;to&nbsp;generate&nbsp;the&nbsp;content&nbsp;of&nbsp;the&nbsp;image?<br><br>Options:<br>A.&nbsp;for&nbsp;x&nbsp;in&nbsp;range(6):<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(x)<br>&nbsp;&nbsp;&nbsp;else:<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print("Finally&nbsp;finished!")<br>&nbsp;&nbsp;&nbsp;<br>B.&nbsp;thisdict&nbsp;=&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"brand":&nbsp;"Ford",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"model":&nbsp;"Mustang",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"year":&nbsp;1964<br>&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;&nbsp;<br>&nbsp;&nbsp;&nbsp;print(len(thisdict))<br>C.&nbsp;x&nbsp;=&nbsp;1<br>&nbsp;&nbsp;&nbsp;y&nbsp;=&nbsp;2.8<br>&nbsp;&nbsp;&nbsp;z&nbsp;=&nbsp;1j<br>&nbsp;&nbsp;&nbsp;<br>&nbsp;&nbsp;&nbsp;print(type(x))<br>&nbsp;&nbsp;&nbsp;print(type(y))<br>&nbsp;&nbsp;&nbsp;print(type(z))<br>&nbsp;&nbsp;&nbsp;<br>D.&nbsp;fruits&nbsp;=&nbsp;["apple",&nbsp;"banana",&nbsp;"cherry"]<br>&nbsp;&nbsp;&nbsp;for&nbsp;x&nbsp;in&nbsp;fruits:<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(x)<br><br>ANSWER.&nbsp;D<br></p></td>
		<td colspan="2"><p>QUESTION.&nbsp;Which&nbsp;one&nbsp;is&nbsp;the&nbsp;correct&nbsp;caption&nbsp;of&nbsp;this&nbsp;image?<br><br>Options:<br>A.&nbsp;A&nbsp;man&nbsp;rides&nbsp;a&nbsp;surfboard&nbsp;on&nbsp;a&nbsp;large&nbsp;wave.<br>B.&nbsp;a&nbsp;young&nbsp;boy&nbsp;barefoot&nbsp;holding&nbsp;an&nbsp;umbrella&nbsp;touching&nbsp;the&nbsp;horn&nbsp;of&nbsp;a&nbsp;cow<br>C.&nbsp;A&nbsp;giraffe&nbsp;standing&nbsp;by&nbsp;a&nbsp;stall&nbsp;in&nbsp;a&nbsp;field.<br>D.&nbsp;A&nbsp;stop&nbsp;sign&nbsp;that&nbsp;has&nbsp;been&nbsp;vandalized&nbsp;with&nbsp;graffiti.<br><br>ANSWER.&nbsp;B<br></p></td>
	</tr>
	<tr>
		<td style="text-align:center;", colspan="2"><b>Coarse Perception:<br>Image Scene</b></td>
		<td style="text-align:center;", colspan="2"><b>Finegrained Perception (instance-level):<br>Object Localization</b></td>
	</tr>
	<tr>
		<td colspan="2"><img src="MMBench/812.jpg"></td>
		<td colspan="2"><img src="MMBench/672.jpg"></td>
	</tr>
	<tr>
		<td colspan="2"><p>QUESTION.&nbsp;Which&nbsp;scene&nbsp;category&nbsp;matches&nbsp;this&nbsp;image&nbsp;the&nbsp;best?<br><br>Options:<br>A.&nbsp;rock_arch<br>B.&nbsp;train_interior<br>C.&nbsp;shopfront<br>D.&nbsp;office_cubicles<br><br>ANSWER.&nbsp;A<br></p></td>
		<td colspan="2"><p>QUESTION.&nbsp;How&nbsp;many&nbsp;trucks&nbsp;are&nbsp;in&nbsp;this&nbsp;photo?<br><br>Options:<br>A.&nbsp;six<br>B.&nbsp;five<br>C.&nbsp;seven<br>D.&nbsp;eight<br><br>ANSWER.&nbsp;A<br></p></td>
	</tr>
	<tr>
		<td style="text-align:center;", colspan="2"><b>Coarse Perception:<br>Image Topic</b></td>
		<td style="text-align:center;", colspan="2"><b>Attribute Reasoning:<br>Function Reasoning</b></td>
	</tr>
	<tr>
		<td colspan="2"><img src="MMBench/2789.jpg"></td>
		<td colspan="2"><img src="MMBench/2705.jpg"></td>
	</tr>
	<tr>
		<td colspan="2"><p>QUESTION.&nbsp;Which&nbsp;of&nbsp;the&nbsp;following&nbsp;captions&nbsp;best&nbsp;describes&nbsp;this&nbsp;image?<br><br>Options:<br>A.&nbsp;A&nbsp;giraffe&nbsp;eating&nbsp;tree&nbsp;leaves&nbsp;in&nbsp;the&nbsp;desert<br>B.&nbsp;A&nbsp;chimpanzee&nbsp;being&nbsp;petted&nbsp;on&nbsp;the&nbsp;head<br>C.&nbsp;A&nbsp;horse&nbsp;drinking&nbsp;water&nbsp;by&nbsp;the&nbsp;shore<br>D.&nbsp;A&nbsp;black&nbsp;puppy&nbsp;and&nbsp;a&nbsp;baby&nbsp;in&nbsp;the&nbsp;snow<br><br>ANSWER.&nbsp;C<br></p></td>
		<td colspan="2"><p>QUESTION.&nbsp;What's&nbsp;the&nbsp;function&nbsp;of&nbsp;the&nbsp;demonstrated&nbsp;object?<br><br>Options:<br>A.&nbsp;Tracking&nbsp;and&nbsp;organizing&nbsp;dates,&nbsp;days,&nbsp;weeks,&nbsp;months,&nbsp;and&nbsp;years.<br>B.&nbsp;Displaying&nbsp;and&nbsp;indicating&nbsp;the&nbsp;current&nbsp;time.<br>C.&nbsp;Reflecting&nbsp;and&nbsp;providing&nbsp;a&nbsp;reflection&nbsp;of&nbsp;the&nbsp;viewer's&nbsp;appearance.<br>D.&nbsp;Providing&nbsp;a&nbsp;comfortable&nbsp;sleeping&nbsp;and&nbsp;resting&nbsp;place.<br><br>ANSWER.&nbsp;A<br></p></td>
	</tr>
	<tr>
		<td style="text-align:center;", colspan="2"><b>Logic Reasoning:<br>Future Prediction</b></td>
		<td style="text-align:center;", colspan="2"><b>Attribute Reasoning:<br>Identity Reasoning</b></td>
	</tr>
	<tr>
		<td colspan="2"><img src="MMBench/2222.jpg"></td>
		<td colspan="2"><img src="MMBench/2368.jpg"></td>
	</tr>
	<tr>
		<td colspan="2"><p>QUESTION.&nbsp;Based&nbsp;on&nbsp;this&nbsp;image,&nbsp;please&nbsp;predict&nbsp;what&nbsp;will&nbsp;happen&nbsp;next?<br><br>Options:<br>A.&nbsp;This&nbsp;egg&nbsp;will&nbsp;become&nbsp;cooked<br>B.&nbsp;This&nbsp;egg&nbsp;will&nbsp;fall&nbsp;down<br>C.&nbsp;The&nbsp;egg&nbsp;will&nbsp;be&nbsp;broken<br><br>ANSWER.&nbsp;C<br></p></td>
		<td colspan="2"><p>QUESTION.&nbsp;What&nbsp;sport&nbsp;are&nbsp;they&nbsp;athletes&nbsp;of?<br><br>Options:<br>A.&nbsp;weightlifting<br>B.&nbsp;diving<br>C.&nbsp;shooting<br>D.&nbsp;gymnastics<br><br>ANSWER.&nbsp;B<br></p></td>
	</tr>
	<tr>
		<td style="text-align:center;", colspan="2"><b>Attribute Reasoning:<br>Physical Property Reasoning</b></td>
		<td style="text-align:center;", colspan="2"><b>Relation Reasoning:<br>Social Relation</b></td>
	</tr>
	<tr>
		<td colspan="2"><img src="MMBench/862.jpg"></td>
		<td colspan="2"><img src="MMBench/1156.jpg"></td>
	</tr>
	<tr>
		<td colspan="2"><p>QUESTION.&nbsp;What&nbsp;properties&nbsp;do&nbsp;the&nbsp;metals&nbsp;in&nbsp;the&nbsp;image&nbsp;have?<br><br>Options:<br>A.&nbsp;Silver&nbsp;white&nbsp;color.<br>B.&nbsp;Good&nbsp;conductivity.<br>C.&nbsp;Aromatic&nbsp;liquid.<br>D.&nbsp;Good&nbsp;flowability.<br><br>ANSWER.&nbsp;B<br></p></td>
		<td colspan="2"><p>QUESTION.&nbsp;What&nbsp;can&nbsp;be&nbsp;the&nbsp;relationship&nbsp;between&nbsp;the&nbsp;two&nbsp;persons&nbsp;in&nbsp;this&nbsp;image?<br><br>Options:<br>A.&nbsp;Father&nbsp;and&nbsp;daughter<br>B.&nbsp;Mother&nbsp;and&nbsp;son<br>C.&nbsp;Brother&nbsp;and&nbsp;sister<br>D.&nbsp;Husband&nbsp;and&nbsp;wife<br><br>ANSWER.&nbsp;B<br></p></td>
	</tr>
	<tr>
		<td style="text-align:center;", colspan="2"><b>Finegrained Perception (instance-level):<br>Attribute Recognition</b></td>
		<td style="text-align:center;", colspan="2"><b>Relation Reasoning:<br>Physical Relation</b></td>
	</tr>
	<tr>
		<td colspan="2"><img src="MMBench/2318.jpg"></td>
		<td colspan="2"><img src="MMBench/2399.jpg"></td>
	</tr>
	<tr>
		<td colspan="2"><p>QUESTION.&nbsp;What&nbsp;is&nbsp;the&nbsp;approximate&nbsp;shape&nbsp;of&nbsp;this&nbsp;umbrella?<br><br>Options:<br>A.&nbsp;Circle<br>B.&nbsp;Octagon<br>C.&nbsp;Triangle<br>D.&nbsp;Rectangle<br><br>ANSWER.&nbsp;B<br></p></td>
		<td colspan="2"><p>QUESTION.&nbsp;Who&nbsp;is&nbsp;closer&nbsp;to&nbsp;the&nbsp;football&nbsp;in&nbsp;the&nbsp;image,&nbsp;the&nbsp;player&nbsp;in&nbsp;the&nbsp;black&nbsp;jersey&nbsp;or&nbsp;the&nbsp;player&nbsp;in&nbsp;the&nbsp;green&nbsp;jersey?<br><br>Options:<br>A.&nbsp;The&nbsp;player&nbsp;in&nbsp;the&nbsp;black&nbsp;jersey.<br>B.&nbsp;The&nbsp;player&nbsp;in&nbsp;the&nbsp;green&nbsp;jersey.<br>C.&nbsp;They&nbsp;are&nbsp;equally&nbsp;close.<br>D.&nbsp;It&nbsp;cannot&nbsp;be&nbsp;determined.<br><br>ANSWER.&nbsp;B<br></p></td>
	</tr>
	<tr>
		<td style="text-align:center;", colspan="2"><b>Relation Reasoning:<br>Nature Relation</b></td>
		<td style="text-align:center;", colspan="2"><b>Finegrained Perception (cross-instance):<br>Attribute Comparison</b></td>
	</tr>
	<tr>
		<td colspan="2"><img src="MMBench/2967.jpg"></td>
		<td colspan="2"><img src="MMBench/318.jpg"></td>
	</tr>
	<tr>
		<td colspan="2"><p>QUESTION.&nbsp;In&nbsp;nature,&nbsp;what's&nbsp;the&nbsp;relationship&nbsp;between&nbsp;these&nbsp;two&nbsp;creatures?<br><br>Options:<br>A.&nbsp;Predatory&nbsp;relationships<br>B.&nbsp;Competitive&nbsp;relationships<br>C.&nbsp;Parasitic&nbsp;relationships<br>D.&nbsp;Mutualistic&nbsp;relationship<br><br>ANSWER.&nbsp;A<br></p></td>
		<td colspan="2"><p>QUESTION.&nbsp;Which&nbsp;solution&nbsp;has&nbsp;a&nbsp;higher&nbsp;concentration&nbsp;of&nbsp;green&nbsp;particles?<br>HINT.&nbsp;The&nbsp;diagram&nbsp;below&nbsp;is&nbsp;a&nbsp;model&nbsp;of&nbsp;two&nbsp;solutions.&nbsp;Each&nbsp;green&nbsp;ball&nbsp;represents&nbsp;one&nbsp;particle&nbsp;of&nbsp;solute.<br><br>Options:<br>A.&nbsp;neither;&nbsp;their&nbsp;concentrations&nbsp;are&nbsp;the&nbsp;same<br>B.&nbsp;Solution&nbsp;B<br>C.&nbsp;Solution&nbsp;A<br><br>ANSWER.&nbsp;B<br></p></td>
	</tr>
	<tr>
		<td style="text-align:center;", colspan="2"><b>Finegrained Perception (cross-instance):<br>Spatial Relationship</b></td>
		<td style="text-align:center;", colspan="2"><b>Finegrained Perception (instance-level):<br>OCR</b></td>
	</tr>
	<tr>
		<td colspan="2"><img src="MMBench/2870.jpg"></td>
		<td colspan="2"><img src="MMBench/1745.jpg"></td>
	</tr>
	<tr>
		<td colspan="2"><p>QUESTION.&nbsp;What&nbsp;direction&nbsp;is&nbsp;Yemen&nbsp;in&nbsp;Saudi&nbsp;Arabia?<br><br>Options:<br>A.&nbsp;east<br>B.&nbsp;west<br>C.&nbsp;north<br>D.&nbsp;south<br><br>ANSWER.&nbsp;D<br></p></td>
		<td colspan="2"><p>QUESTION.&nbsp;What&nbsp;does&nbsp;this&nbsp;picture&nbsp;want&nbsp;to&nbsp;express?<br><br>Options:<br>A.&nbsp;We&nbsp;are&nbsp;expected&nbsp;to&nbsp;care&nbsp;for&nbsp;green&nbsp;plants.<br>B.&nbsp;We&nbsp;are&nbsp;expected&nbsp;to&nbsp;care&nbsp;for&nbsp;the&nbsp;earth.<br>C.&nbsp;We&nbsp;are&nbsp;expected&nbsp;to&nbsp;stay&nbsp;positive.<br>D.&nbsp;We&nbsp;are&nbsp;expected&nbsp;to&nbsp;work&nbsp;hard.<br><br>ANSWER.&nbsp;B<br></p></td>
	</tr>
	<tr>
		<td style="text-align:center;", colspan="2"><b>Finegrained Perception (instance-level):<br>Celebrity Recognition</b></td>
		<td style="text-align:center;", colspan="2"><b>Coarse Perception:<br>Image Style</b></td>
	</tr>
	<tr>
		<td colspan="2"><img src="MMBench/718.jpg"></td>
		<td colspan="2"><img src="MMBench/503.jpg"></td>
	</tr>
	<tr>
		<td colspan="2"><p>QUESTION.&nbsp;Who&nbsp;is&nbsp;the&nbsp;person&nbsp;in&nbsp;this&nbsp;image?<br><br>Options:<br>A.&nbsp;Jackie&nbsp;Chan<br>B.&nbsp;Jing&nbsp;Wu<br>C.&nbsp;Donald&nbsp;Trump<br>D.&nbsp;Steve&nbsp;Jobs<br><br>ANSWER.&nbsp;D<br></p></td>
		<td colspan="2"><p>QUESTION.&nbsp;Which&nbsp;can&nbsp;be&nbsp;the&nbsp;associated&nbsp;text&nbsp;with&nbsp;this&nbsp;image&nbsp;posted&nbsp;on&nbsp;twitter<br><br>Options:<br>A.&nbsp;I&nbsp;painted&nbsp;a&nbsp;picture&nbsp;of&nbsp;sushi.&nbsp;It's&nbsp;a&nbsp;colorful&nbsp;and&nbsp;tasty&nbsp;scene.<br>B.&nbsp;look&nbsp;at&nbsp;this&nbsp;cute&nbsp;toy&nbsp;sushi&nbsp;set&nbsp;🥹<br>C.&nbsp;St.&nbsp;Louis&nbsp;Sushi&nbsp;(ham&nbsp;wrapped&nbsp;around&nbsp;cream&nbsp;cheese&nbsp;and&nbsp;a&nbsp;pickle)<br>D.&nbsp;Perfect&nbsp;Sushi&nbsp;Cake&nbsp;with&nbsp;Fresh&nbsp;Salmon&nbsp;and&nbsp;Avocado&nbsp;A&nbsp;sushi&nbsp;cake&nbsp;is&nbsp;a&nbsp;unique&nbsp;twist&nbsp;on&nbsp;traditional&nbsp;sushi&nbsp;that&nbsp;is&nbsp;perfect&nbsp;for&nbsp;special&nbsp;occasions&nbsp;or&nbsp;a&nbsp;fun&nbsp;meal&nbsp;with&nbsp;friends&nbsp;and&nbsp;family.&nbsp;#SushiCake&nbsp;#salmonavocado&nbsp;#avocado&nbsp;#avocadotoast&nbsp;#cake&nbsp;#recipe&nbsp;#dinner&nbsp;#food&nbsp;#FoodieBeauty<br><br>ANSWER.&nbsp;A<br></p></td>
	</tr>
	<tr>
		<td style="text-align:center;", colspan="2"><b>Coarse Perception:<br>Image Emotion</b></td>
		<td style="text-align:center;", colspan="2"><b>Coarse Perception:<br>Image Quality</b></td>
	</tr>
	<tr>
		<td colspan="2"><img src="MMBench/544.jpg"></td>
		<td colspan="2"><img src="MMBench/768.jpg"></td>
	</tr>
	<tr>
		<td colspan="2"><p>QUESTION.&nbsp;Identify&nbsp;the&nbsp;emotion&nbsp;expressed&nbsp;in&nbsp;this&nbsp;image.<br><br>Options:<br>A.&nbsp;happiness<br>B.&nbsp;sadness<br>C.&nbsp;anger<br>D.&nbsp;love<br><br>ANSWER.&nbsp;A<br></p></td>
		<td colspan="2"><p>QUESTION.&nbsp;Which&nbsp;image&nbsp;is&nbsp;the&nbsp;brightest&nbsp;one?<br><br>Options:<br>A.&nbsp;upper&nbsp;left<br>B.&nbsp;upper&nbsp;right<br>C.&nbsp;down&nbsp;left<br>D.&nbsp;down&nbsp;right<br><br>ANSWER.&nbsp;C<br></p></td>
	</tr>
</table>

