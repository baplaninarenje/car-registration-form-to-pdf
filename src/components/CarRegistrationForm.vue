<template>
    <div class="top">
        <h1 id="main-heading">Zapisnik o vrsenju tehnickog pregleda vozila</h1>
        <div class="tables-container">
            <div class="tables-left-group">
                <table class="table-item">
                    <tr>
                        <td>ID broj</td>
                        <td><input type="text"></td>
                    </tr>
                    <tr>
                        <td>Datum</td>
                        <td><input type="text"></td>
                    </tr>
                    <tr>
                        <td>Vreme pocetka</td>
                        <td><input type="text"></td>
                    </tr>
                    <tr>
                        <td>Vreme zavrsetka</td>
                        <td><input type="text"></td>
                    </tr>
                </table>
                <table class="table-item">
                    <caption class="small">Ispunjenost uslova za vrsenje tehnickog pregleda vozila</caption>
                    <tr>
                        <td>
                            <input type="radio" name="ispunjenost-uslova" value="Da">
                            <label>Da</label>
                        </td>
                        <td>
                            <input type="radio" name="ispunjenost-uslova" value="Ne">
                            <label>Ne</label>
                        </td>
                    </tr>
                </table>
                <table class="table-item">
                    <caption class="large">Podaci o stranci</caption>
                    <tr>
                        <td>Ime i prezime</td>
                        <td><input type="text"></td>
                    </tr>
                    <tr>
                        <td>Registarski broj licne karte stranke, odnosno drugog dokumenta za strance</td>
                        <td><input type="text"></td>
                    </tr>
                </table>
            </div>
            <div class="tables-right-group">
                <table class="table-item">
                    <tr>
                        <td>S.1</td>
                        <td>Broj mesta za sedenje</td>
                        <td colspan="2"><input type="text"></td>
                    </tr>
                    <tr>
                        <td>S.2</td>
                        <td>Broj mesta za stajanje</td>
                        <td colspan="2"><input type="text"></td>
                    </tr>
                    <tr>
                        <td>B.1</td>
                        <td>Godina proizvodnje vozila</td>
                        <td colspan="2"><input type="text"></td>
                    </tr>
                    <tr>
                        <td class="rotated" rowspan="6">Oznake pneumatika <sup>6</sup></td>
                        <td>Levo</td>
                        <td colspan="2">Desno</td>
                    </tr>
                    <tr>
                        <td><label>1.</label><input type="text"></td>
                        <td colspan="2"><label>1.</label><input type="text"></td>
                    </tr>
                    <tr>
                        <td><label>2.</label><input type="text"></td>
                        <td colspan="2"><label>2.</label><input type="text"></td>
                    </tr>
                    <tr>
                        <td><label>3.</label><input type="text"></td>
                        <td colspan="2"><label>3.</label><input type="text"></td>
                    </tr>
                    <tr>
                        <td><label>4.</label><input type="text"></td>
                        <td colspan="2"><label>4.</label><input type="text"></td>
                    </tr>
                    <tr>
                        <td><label>5.</label><input type="text"></td>
                        <td colspan="2"><label>5.</label><input type="text"></td>
                    </tr>

                    <tr>
                        <td rowspan="3">DV</td>
                        <td rowspan="3">Dimenzije (m)<sup>7</sup></td>
                        <td class="dimenzije-right-padding">D</td>
                        <td><input type="text"></td>
                    </tr>

                    <tr>
                        <td>S</td>
                        <td><input type="text"></td>
                    </tr>

                    <tr>
                        <td>V</td>
                        <td><input type="text"></td>
                    </tr>
                </table>
            </div>
        </div>
    </div>
</template>

<style>
.top {
    height: 100%
}

.tables-container {
    text-align: center;
    height: 100%;
}

#main-heading {
    text-align: center;
    margin: 30px 0;
    text-decoration: underline;
}

.tables-left-group,
.tables-right-group {
    display: inline-block;
    width: 40%;
    height: 100%;
    margin: auto;
    text-align: left;
}

.tables-left-group {
    margin-right: 20px;
}

.tables-right-group {
    margin-left: 20px
}

.table-item {
    border-spacing: 0;
    border-collapse: collapse;
    width: 100%;
    margin-top: 40px;
}

td {
    border: solid 1px black;
    padding: 3px;
}

td:has(> input) {
    text-align: center;
}

input[type="text"] {
    border: 1px solid transparent;
    outline: none;
    width: 90%;
    height: 90%;
}

input[type=text]:focus {
    border: lightblue solid 1px;
    background-color: rgba(218, 241, 248, .1)
}

label {
    margin: 0 2px;
}

caption {
    text-align: left;
}

caption.small {
    font-weight: bold;
    margin-bottom: 2px;
}

caption.large {
    font-weight: bold;
    margin-bottom: 8px;
    font-size: 23px;
}

.rotated {
    writing-mode: tb-rl;
    transform: rotate(-180deg);
}

.dimenzije-right-padding {
    padding-right: 20px;
}
</style>