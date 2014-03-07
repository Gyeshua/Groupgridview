Groupgridview
=============


$this->widget('bootstrap.widgets.TbGroupGridView', array(
      'id' => 'grid1',
      'itemsCssClass'=>'table table-bordered table-condensed',
      'dataProvider' => $model->search(),
	'enableSorting'=>false,
	'summaryText'=>'',
      //'extraRowColumns' => array('register_id'),
	  //'extraRowExpression'=> 'sadfsdf',
     /* 'extraRowTotals'=>function() {
		   $model->candidate_register->name;  date('Y-m-d', strtotime($datetime))
	  },*/
	  'mergeColumns' => array('register_id'),
	  'mergeType' => 'nested',	
      'columns' => array(
        array('header'=>'Name','type'=>'raw','name'=>'register_id','value'=>'$data->candidate_register->name'),
	array('header'=>'Exam Date','type'=>'raw','name'=>'register_id','value'=>'date("d/m/Y",strtotime($data->candidate_register->createdon))'),
array('header'=>'Exam Title','name'=>'question_category_id','value'=>'$data->question_category->title'),
	//array('header'=>'Exam','name'=>'selection_id','value'=>'$data->selection_process->title'),
        'mark',
        'result',
		/*array(
			'name' => 'register_id',
			'header' => 'Feedback',
			'value'=> '$data->candidate_register->interview_feedback == ""? "Empty" : $data->candidate_register->interview_feedback',
			),
			array(
			'name' => 'register_id',
			'header' => 'Interview Status',
			'class' => 'bootstrap.widgets.TbEditableColumn',
			'editable' => array( 
						'type'  => 'select',
						'source'=> array('Selected', 'Rejected', 'On Hold'),
						'url' => $this->createUrl('CandidateRegister/inupdate&status'),
						//'placement' => 'right',
						),
			
			//'value'=> '$data->candidate_register->interview_status == ""? "Empty" : $data->candidate_register->interview_status',
			),*/

			array(            
            'name'=>'Entered By',
            //call the method 'gridDataColumn' from the controller
            'value'=>array($this,'gridDataColumn'), 
        ),
			
			
			array(
			'name' => 'register_id',
			'header' => 'Note',
			'class' => 'bootstrap.widgets.TbEditableColumn',
			//'headerHtmlOptions' => array('style' => 'width: 200px'),
			'editable' => array( 
						'type'  => 'textarea',
						'url' => $this->createUrl('CandidateRegister/inupdate&note'),
						'placement' => 'right',
						  'title'     => 'Enter Notes',
						),
			
			'value'=> '$data->candidate_register->interview_notes == ""? "Empty" : $data->candidate_register->interview_notes',
			), 
			
			
			/*array(
		'name' => 'register_id',
		'header' => 'Feedback',
		'type' => 'raw',
		'class' => 'bootstrap.widgets.TbEditableColumn',
		'editable' => array( 
					'type'  => 'textarea',
					'url' => $this->createUrl('CandidateRegister/InUpdate&feedback'),
					'placement' => 'right',
					),
		'value'=>'($data->candidate_register->interview_feedback=="")?("Empty"):($data->candidate_register->interview_feedback)'
		//'value'=>'$data->candidate_feedback->feedback',
		),*/
		/*array(
			'name' => 'register_id',
			'header' => 'Status',
			'class' => 'bootstrap.widgets.TbEditableColumn',
			//'filter'=>CHtml::DropDownList('CandidateExamDetails[status]', 'status',
//								array('Selected'=>'Selected','Rejected'=>'Rejected','On Hold'=>'On Hold'),
//								array('style'=>'width:auto;','prompt'=>'Select')),
			'headerHtmlOptions' => array('style' => ''),
			//'editable' => array('type' => 'select',
//								'source'=> array('Selected', 'Rejected', 'On Hold'),
//								'url'=> $this->createUrl('CandidateFeedback/inupdate&status'),
//								),
			
		),*/
		/*array(
			'name' => 'register_id',
			'header' => 'Note',
			'class' => 'bootstrap.widgets.TbEditableColumn',
			'headerHtmlOptions' => array('style' => 'width: 200px'),
			'editable' => array( 
						'type'  => 'textarea',
						'url' => $this->createUrl('CandidateRegister/inupdate&note'),
						'placement' => 'right',
						),
			
			'value'=>'$data->candidate_register->interview_notes',
			),*/
		/*array(
			'class'=>'CButtonColumn',
			'template'=>'{view} {delete}',
			'buttons'=>array(
			'view'=>array(
			'url'=>'Yii::app()->controller->createUrl("candidateRegister/update",array("id"=>$data->primaryKey))'
			)
			)
		),*/
		
		
		 array(
        'name'  => 'register_id',
		'header' => '',
        'value' => 'CHtml::link("View Details",Yii::app()->createUrl("candidateRegister/update",array("id"=>$data->primaryKey)))',
        'type'  => 'raw',
    ),
		
      ),
    ));


?>
