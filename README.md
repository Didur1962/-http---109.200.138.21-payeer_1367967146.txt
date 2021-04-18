# -http---109.200.138.21-payeer_1367967146.txt ?php
require_once('cpayeer.php');
$accountNumber = 'P1032682253';
$apiId = '1363037844';
$apiKey = '****************';
$payeer = new CPayeer($accountNumber, $apiId, $apiKey);
if ($payeer->isAuth())
{
	$arTransfer = $payeer->transfer(array(
		'curIn' => 'USD',
		'sum' => 1,
		'curOut' => 'USD',
		//'sumOut' => 1,
		'to' => 'P1000000',
		//'to' => 'client@mail.com',
		//'comment' => 'test',
		//'protect' => 'Y',
		//'protectPeriod' => '3',
		//'protectCode' => '12345',
	));
	if (empty($arTransfer['errors']))
	{
		echo $arTransfer['historyId'].": Перевод средств успешно выполнен";
	}
	else
	{
		echo '<pre>'.print_r($arTransfer["errors"], true).'</pre>';
	}
}
else
{
	echo '<pre>'.print_r($payeer->getErrors(), true).'</pre>';
}
?>
