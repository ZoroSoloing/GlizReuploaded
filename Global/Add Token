//  --> PLEASE READ THIS!!! <---
//  
//  Do not change the numbers in this file! Blooket has a hard limit on how many tokens
//  you can add everyday. The limit is 500 and you cannot bypass it. Do not mess with
//  with this file if you do not know what you are doing!!!
//


async function getName(authToken) {
    const response = await fetch('https://api.blooket.com/api/users/verify-token?token=JWT+' + authToken);
    const data = await response.json();

    return data.name
};

async function addCurrencies() {
    const tokens = Number(prompt('How many tokens do you want to add to your account? (500 daily)'));
    const myToken = localStorage.token.split('JWT ')[1];

    if (tokens > 500) {
        alert('You can only add up to 500 tokens daily.')
    }

    const response = await fetch('https://api.blooket.com/api/users/add-rewards', {
        method: "PUT",
        headers: {
            "referer": "https://www.blooket.com/",
            "content-type": "application/json",
            "authorization": localStorage.token
        },
        body: JSON.stringify({
            addedTokens: tokens,
            addedXp: 300,
            name: await getName(myToken)
        })
    });

    if (response.status == 200) {
        alert(`${tokens} tokens and 300 XP added to your account!`);
    } else {
        alert('An error occured.');
    };

};

addCurrencies();
