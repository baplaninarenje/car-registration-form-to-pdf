<template>
    <div class="app-container" id="pdf-content">
        <h1 id="main-heading">Zapisnik o vrsenju tehnickog pregleda vozila</h1>
        <div class="tables-container">
            <div class="tables-left-group">
                <table class="table-item">
                    <tbody>
                        <tr>
                            <td>ID broj</td>
                            <td><input v-model="formData.id" type="text" name="id" id="id"></td>
                        </tr>
                        <tr>
                            <td>Datum</td>
                            <td><input v-model="formData.date" type="text" name="date" id="date"></td>
                        </tr>
                        <tr>
                            <td>Vreme pocetka</td>
                            <td><input v-model="formData.startTime" type="text" name="startTime" id="startTime"></td>
                        </tr>
                        <tr>
                            <td>Vreme zavrsetka</td>
                            <td><input v-model="formData.endTime" type="text" name="endTime" id="endTime"></td>
                        </tr>
                    </tbody>
                </table>

                <table class="table-item">
                    <caption class="small">Ispunjenost uslova za vrsenje tehnickog pregleda vozila</caption>
                    <tbody>
                        <tr>
                            <td>
                                <input v-model="formData.technicalCheck" type="radio" name="technicalCheck" value="Da"
                                    id="technicalCheckYes">
                                <label for="technicalCheckYes">Da</label>
                            </td>
                            <td>
                                <input v-model="formData.technicalCheck" type="radio" name="technicalCheck" value="Ne"
                                    id="technicalCheckNo">
                                <label for="technicalCheckNo">Ne</label>
                            </td>
                        </tr>
                    </tbody>
                </table>

                <table class="table-item">
                    <caption class="large">Podaci o stranci</caption>
                    <tbody>
                        <tr>
                            <td>Ime i prezime</td>
                            <td><input v-model="formData.fullName" type="text" name="fullName" id="fullName"></td>
                        </tr>
                        <tr>
                            <td>Registarski broj licne karte stranke</td>
                            <td><input v-model="formData.idCardNumber" type="text" name="idCardNumber"
                                    id="idCardNumber"></td>
                        </tr>
                    </tbody>
                </table>
            </div>

            <div class="tables-right-group">
                <table class="table-item">
                    <thead>
                        <tr>
                            <td>S.1</td>
                            <td>Broj mesta za sedenje</td>
                            <td colspan="2"><input v-model="formData.seatingCapacity" type="text" name="seatingCapacity"
                                    id="seatingCapacity"></td>
                        </tr>
                        <tr>
                            <td>S.2</td>
                            <td>Broj mesta za stajanje</td>
                            <td colspan="2"><input v-model="formData.standingCapacity" type="text"
                                    name="standingCapacity" id="standingCapacity"></td>
                        </tr>
                        <tr>
                            <td>B.1</td>
                            <td>Godina proizvodnje vozila</td>
                            <td colspan="2"><input v-model="formData.manufactureYear" type="text" name="manufactureYear"
                                    id="manufactureYear"></td>
                        </tr>
                    </thead>

                    <tbody>
                        <tr>
                            <td class="rotated" rowspan="6">Oznake pneumatika <sup>6</sup></td>
                            <td>Levo</td>
                            <td colspan="2">Desno</td>
                        </tr>
                        <tr>
                            <td><label for="leftTire1">1.</label><input v-model="formData.leftTire[0]" type="text"
                                    id="leftTire1"></td>
                            <td colspan="2"><label for="rightTire1">1.</label><input v-model="formData.rightTire[0]"
                                    type="text" id="rightTire1"></td>
                        </tr>
                        <tr>
                            <td><label for="leftTire2">2.</label><input v-model="formData.leftTire[1]" type="text"
                                    id="leftTire2"></td>
                            <td colspan="2"><label for="rightTire2">2.</label><input v-model="formData.rightTire[1]"
                                    type="text" id="rightTire2"></td>
                        </tr>
                        <tr>
                            <td><label for="leftTire3">3.</label><input v-model="formData.leftTire[2]" type="text"
                                    id="leftTire3"></td>
                            <td colspan="2"><label for="rightTire3">3.</label><input v-model="formData.rightTire[2]"
                                    type="text" id="rightTire3"></td>
                        </tr>
                        <tr>
                            <td><label for="leftTire4">4.</label><input v-model="formData.leftTire[3]" type="text"
                                    id="leftTire4"></td>
                            <td colspan="2"><label for="rightTire4">4.</label><input v-model="formData.rightTire[3]"
                                    type="text" id="rightTire4"></td>
                        </tr>
                        <tr>
                            <td><label for="leftTire5">5.</label><input v-model="formData.leftTire[4]" type="text"
                                    id="leftTire5"></td>
                            <td colspan="2"><label for="rightTire5">5.</label><input v-model="formData.rightTire[4]"
                                    type="text" id="rightTire5"></td>
                        </tr>

                        <tr>
                            <td rowspan="3">DV</td>
                            <td rowspan="3">Dimenzije (m)<sup>7</sup></td>
                            <td class="dimenzije-right-padding">D</td>
                            <td><input v-model="formData.dimensions.d" type="text" id="dimensionD"></td>
                        </tr>
                        <tr>
                            <td>S</td>
                            <td><input v-model="formData.dimensions.s" type="text" id="dimensionS"></td>
                        </tr>
                        <tr>
                            <td>V</td>
                            <td><input v-model="formData.dimensions.v" type="text" id="dimensionV"></td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
        <button class="pdf-btn" @click="exportToPDF">Preuzmi kao PDF</button>
    </div>
</template>

<script>
import jsPDF from 'jspdf';
import html2canvas from 'html2canvas';


export default {
    data() {
        return {
            formData: {
                id: '',
                date: '',
                startTime: '',
                endTime: '',
                technicalCheck: '',
                fullName: '',
                idCardNumber: '',
                seatingCapacity: '',
                standingCapacity: '',
                manufactureYear: '',
                leftTire: ['', '', '', '', ''],
                rightTire: ['', '', '', '', ''],
                dimensions: {
                    d: '',
                    s: '',
                    v: '',
                },
            }
        };
    },
    methods: {
        exportToPDF() {
            const pdfButton = document.querySelector('.pdf-btn');
            pdfButton.style.visibility = 'hidden';

            const form = document.getElementById('pdf-content');
            html2canvas(form).then((canvas) => {
                const imgData = canvas.toDataURL('image/png');
                const imgWidth = 210; // A4 width in mm (for portrait mode)
                const pageHeight = 297; // A4 height in mm
                const imgHeight = (canvas.height * imgWidth) / canvas.width; // Maintain the aspect ratio
                let heightLeft = imgHeight;

                const doc = new jsPDF('p', 'mm', 'a4');
                let position = 10;

                doc.addImage(imgData, 'PNG', 10, position, imgWidth - 20, imgHeight);
                heightLeft -= pageHeight;

                // Add additional pages if the content overflows
                while (heightLeft >= 0) {
                    position = heightLeft - imgHeight;
                    doc.addPage();
                    doc.addImage(imgData, 'PNG', 10, position, imgWidth - 20, imgHeight);
                    heightLeft -= pageHeight;
                }

                doc.save('tehnicki_pregled.pdf');
                pdfButton.style.visibility = 'visible';
            });
        },
    }
};
</script>


<style>
.app-container {
    height: 100%;
    font-family: Arial, sans-serif;
    font-size: 16px;
    line-height: 1.5;
}

.tables-container {
    text-align: center;
}

#main-heading {
    text-align: center;
    margin: 30px 0;
    text-decoration: underline;
    font-size: 21px;

}

.tables-left-group,
.tables-right-group {
    display: inline-block;
    width: 40%;
    margin: 0 2%;
    vertical-align: top;
}

.table-item {
    border-spacing: 0;
    border-collapse: collapse;
    width: 100%;
    margin-top: 52px;
}

td {
    border: solid 1px black;
    padding: 2px 3px;
    text-align: left;
    font-size: 16px;

}

td:has(> input) {
    text-align: center;
}

input[type="text"] {
    border: 1px solid transparent;
    outline: none;
    width: 100%;
    height: 90%;
}

input[type=text]:focus {
    border: lightblue solid 1px;
    background-color: rgba(218, 241, 248, .1);
}

label+input[type="text"] {
    width: 90%;
}

label {
    margin: 0 2px;
    font-size: 16px;
}

caption {
    text-align: left;
}

caption.small {
    font-weight: bold;
    margin-bottom: 2px;
    font-size: 16px;
}

caption.large {
    font-weight: bold;
    margin-bottom: 8px;
    font-size: 18px;

}

.rotated {
    writing-mode: tb-rl;
    transform: rotate(-180deg);
}

.dimenzije-right-padding {
    padding-right: 20px;
}

button {
    display: block;
    margin: 50px auto;
    padding: 10px 20px;
    background-color: #4CAF50;
    color: white;
    border: 2px solid #4CAF50;
    border-radius: 12px;
    cursor: pointer;
    clear: both;
    font-size: 16px;
}

button:hover {
    background-color: white;
    color: #4CAF50;
}
</style>
