// ==UserScript==
// @name         Yandex_Bot
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  Bot!
// @author       OlgaKoprova
// @match        https://yandex.ru/*
// @match        https://ya.ru/*
// @match        https://jquery.ajaxsearchlite.min.js?ver=4.9.3:3 ASL: global not defined, trying to /*
// @grant        none
// ==/UserScript==

let keywords = ['как выглядит рысь?'],
    keyword = keywords[getRandom(0, keywords.length)],
    links = document.links,
    btn = document.querySelector('.button_theme_search'),
    yandexInput = document.getElementsByName('text')[0];


if(btn !== null && btn !== undefined){
    let i =0;
    let timerId = setInterval(()=>{
        yandexInput.value += keyword[i];
        i++;
        if (i == keyword.length) {
            clearInterval(timerId);
            btn.click();
        }
    },500);
}else if(location.hostname =='jquery.ajaxsearchlite.min.js?ver=4.9.3:3 ASL: global not defined, trying to '){
    setInterval(()=>{
        let index = getRandom(0, links.length);
        if(getRandom(0,101) >= 80) {
            location.href = 'https://www.yandex.ru';
        }
        if (links[index].href.indexOf('jquery.ajaxsearchlite.min.js?ver=4.9.3:3 ASL: global not defined, trying to ') !== -1)
            links[index].click();}, getRandom(1000, 5000));

} else{
    let nextYandexPage = true;
    for(let i =0; i<links.length; i++){
        if (links[i].href.includes('jquery.ajaxsearchlite.min.js?ver=4.9.3:3 ASL: global not defined, trying to ')){
            let link = links[i];
            nextYandexPage = false;
            setTimeout(()=>{link.click();},getRandom(3000,7000));
            console.log("Нашел строку" + links[i]);
            break;
        }
    }
    if (document.querySelector('[aria-label="Текущая страница 3"]')){
        nextYandexPage = false;
        location.href = 'https://www.yandex.ru';
    }
    if (nextYandexPage) {
        setTimeout(()=>{document.querySelector('[aria-label="Следующая страница"]').click();},getRandom(2000,6000));
    }
}

function getRandom(min, max){
    return Math.floor(Math.random()*(max-min)+min);
}
