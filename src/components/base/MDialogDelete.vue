<template>
        <!-- dialog input -->
        <div class="dialog " tabindex="-1" @keydown.enter="isDeleteEmployee" @keydown.esc="hideDialog" ref="dialogDelete" >
            <div class="dialog__container content__center">
              <div class="dialog__content dialog__delete">
                <div class="dialog__header">
               
                </div>
                <div class="dialog__body align__items__center">
                     
                        <div class=" icon__warning"></div>
                     
                    <div class="dialog__body__text">
                     {{textDelete}} {{employeeCode}}
                    </div>
                </div>
                <div class="dialog__footer align__items__center dialog__footer-delete">
                    <div class="btn__base content__center" 
                     v-tooltip="'Ấn ESC để chọn Không '"
                    @click="hideDialog" @keypress.enter="hideDialog"> Không </div>
                    <div class="btn  content__center"
                     v-tooltip="'Ấn Enter để chọn Có '"
                     @click="isDeleteEmployee" @dblclick.stop @click.stop>Có</div>
                </div>
              </div>
            </div>
        
        </div>
 
</template>
<script>
import Enum from '../../script/common/enumeration'
export default {
   name : 'DialogDelete',
   props:{
    employeeCode : String,
   },
   emits:['hideDialogDelete','handleDeleteEmployee'],
   methods:{
     /*
     * Hàm dùng  để ẩn  Dialog xóa
     * PCTUANANH(17/09/2022)
     */
    hideDialog(){
        try {
             this.$emit("hideDialogDelete");
        } catch (error) {
            console.log(error);
        }
       
    },
    /*
     * Hàm dùng  để xóa nhân viên 
     * PCTUANANH(17/09/2022)
     */
    isDeleteEmployee(){
        try {
             this.$emit("handleDeleteEmployee");
        } catch (error) {
            console.log(error);
        }
       
    }
   },
    mounted(){
    this.$refs.dialogDelete.focus();
   },
   data() {
    return {
        textDelete : Enum.textDelete
    }
   },
}
</script>