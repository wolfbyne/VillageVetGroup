<script>
	import { functions } from './firebase';

    let currentDate = new Date();
    let cDay = currentDate.getDate();
    let cMonth = currentDate.getMonth() + 1;
    let cYear = currentDate.getFullYear();
    let date = cDay + "/" + cMonth + "/" + cYear;

    let obj = localStorage.getItem("delivery");
    let deliveryDeets = JSON.parse(obj);

    let objItems = localStorage.getItem("data");
    let cartItems = JSON.parse(objItems);

    let num = sessionStorage.getItem("itemName").toString();
    let name
    let mail
    let total = parseInt(localStorage.getItem("total"));
    let deliveryFee = 0
    if(deliveryDeets){
        if(deliveryDeets.deliver){
            deliveryFee = 55
            total += 55;
            name = deliveryDeets.name
            mail = deliveryDeets.email
        }else{
            name = deliveryDeets.name
            mail = deliveryDeets.email
        }
    }

    let html = `<table class='tg' style='undefined;table-layout: fixed; width: 800px'><colgroup><col style='width: 200px'><col style='width: 200px'>
                    <col style='width: 200px'>
                    <col style='width: 200px'>
                    </colgroup>`;

    for(var i = 0; i < cartItems.length; i++){
        html += `<thead> <tr>
                <th class='tg-0lax'>${cartItems[i].id}</th>
                <th class='tg-0lax'>${cartItems[i].name}</th>
                <th class='tg-0lax'>${cartItems[i].units}</th>
                <th class='tg-0lax'>${cartItems[i].price}</th>
                </tr></thead>`;
    }              

    html += '</table>';

	function sendEmail() {
		const callable = functions.httpsCallable('sendAway');
		return callable({mail: mail, ccMail: 'gordonfleming@pm.me', num: num, name: name, date: date, html: html, deliveryFee: deliveryFee, total: total}).then(console.log);
	}
</script>
<h2>SendGrid Transactional Email with Svelte</h2>
<button on:click={() => sendEmail()}>Send Email with Callable Function</button>
